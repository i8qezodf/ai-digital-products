# 单元测试生成器

## 模板

```
请为以下代码生成单元测试：

## 代码信息

**语言/框架：**
[如 Python/pytest, JavaScript/Jest, Go/testing]

**测试类型：**
[单元测试/集成测试/端到端测试]

**代码功能：**
[简要描述代码做什么]

**代码：**
```[语言]
[粘贴代码]
```

## 依赖/导入
[如有特殊依赖]

## 请生成

### 测试框架选择
[推荐使用的测试框架]

### 测试用例

```[语言]
// 测试用例1：正常情况
test('[场景描述]', () => {
  // given
  const input = [输入值];
  const expected = [期望值];
  
  // when
  const result = [调用的函数](input);
  
  // then
  expect(result).toBe(expected);
});

// 测试用例2：边界情况
test('[边界场景]', () => {
  // given
  const input = [边界值];
  
  // when
  const result = [调用的函数](input);
  
  // then
  expect(result).toBe([期望值]);
});

// 测试用例3：错误处理
test('[错误场景]', () => {
  // given
  const input = [无效输入];
  
  // when & then
  expect([调用的函数](input)).toThrow([错误类型]);
});
```

### 覆盖率目标

- 行覆盖率：X%
- 分支覆盖率：X%
- 函数覆盖率：X%

### Mock建议
[如有外部依赖，需要如何Mock]

### 运行测试命令
[测试命令]
```

## 使用说明

1. 粘贴真实可运行的代码
2. 包含足够的边界测试
3. 测试要独立，不相互依赖
4. 包含有意义的测试描述
