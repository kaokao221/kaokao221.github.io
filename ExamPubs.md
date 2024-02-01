# 成绩册帮助

> ###### 写在之前
> 请先到[这里](https://kaokao221.github.io/HarmonyOS_Sans_SC.zip ':download')下载字体包，然后重新打开成绩册。

> 需要注意的是，由于`LAMBDA`、`LET`的存在，截止目前，成绩册的部分区域在`Office 2021`或`Office 2301`之前的版本中可能会大面积出现`#NAME`错误，可以尝试使用`Office for Web`来规避这部分问题。

成绩册的编制依照大部分学校的要求，具备基本的通用性，但没有高度针对性优化，且需要完善。

## 预置名称
你可以在这里找到所有在成绩册中已经定义的名称的解释

### `AVILIABLE600SCORE`
这是实际计算中使用的600分线，引用为：
```Excel
=IF(
    Init600Score=0,
    600,
    Init600Score
)
```
默认是600分，当定义的[`Init600Score`](#Init600Score)存在值时，使用这个值。
参见[`Init600Score`](#Init600Score)

### `ExamName`
这是本次考试的名称，你可以在`配置基本设置`中找到它。

### `filename`
这是工作簿的名称，使用`CELL`定义，引用为:
```Excel
=IFERROR(
    INDEX(
        TEXTSPLIT(
            INDEX(
                TEXTSPLIT(
                    CELL("filename"),
                    "[",
                    "/"
                ),
                ROWS(
                    TEXTSPLIT(
                        CELL("filename"),
                        "[",
                        "/"
                    )
                ),
                2),
                "."
            ),
            1,
            1
    ),
    "请保存文件，在此之前请不要开始操作"
)
```
在保存之前，会显示固定字符，保存后会展示文件名称。

已经验证，在网页版和移动版中，由于不支持`CELL`，也会给出固定字符。因此，建议在之后手动修改该名称的值。

### `HisALess`
这是历史方向特控线临界生计算时线上的分值，你可以在`配置基本设置`中找到它。

### `HisAMore`
这是历史方向特控线临界生计算时线下的分值，你可以在`配置基本设置`中找到它。

## `LAMBDA`公式
你可以在这里找到所有在成绩册中已经定义的`LAMBDA`公式的原始值和解释。

### 