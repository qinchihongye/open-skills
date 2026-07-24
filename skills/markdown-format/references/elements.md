# 元素速查（通用挂载写法）

* 下列片段都假设：已在某个标题下，且从**顶格 `*`** 起笔

## 链接

* 重要资料建议双写

  ```markdown
  * [显示文字](https://example.com/path)

    >https://example.com/path
  ```

## 代码

* 标准挂载

  ````markdown
  * 代码

    ```python
    def main():
        pass
    ```

    ---
  ````

* 语言标签常用：`python` `bash` `json` `text` `mermaid` `sql` `yaml`；未知用 `text`

## 流程图

* 主流程

  ````markdown
  * 主流程

    ```mermaid
    flowchart TD
      A[开始] --> B[结束]
    ```
  ````

## 表格

* 字段说明

  ```markdown
  * 字段说明

    | 字段名 | 类型 | 说明 |
    | ------ | ---- | ---- |
    | id | string | 标识 |

    > 补充：……
  ```

## 公式

* 行内

  ```markdown
  * 维度为 $d_{model}$，位置为 $pos$。
  ```

* 行外

  ```markdown
  * 定义如下。

    $$
    y = Wx + b
    $$

    其中 $W$ 为权重，$b$ 为偏置。
  ```

## 图片

* 步骤配图

  ```markdown
  * 打开设置

    ![image-20250101000000](https://example.com/a.png)

    确认结果

    ![image-20250101000001](https://example.com/b.png)
  ```

## 编号解析

* 挂在 `*` 下

  ```markdown
  * 主要逻辑
    1. **步骤甲**：……
    2. `func_name` 负责……
    3. 输出字段 `foo` 表示……
  ```

## 引用说明

* 挂在 `*` 下，不要顶在标题下

  ```markdown
  * 说明
    > 注意边界条件与默认值。
  ```
