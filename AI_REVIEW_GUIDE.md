# AI代码审查配置指南

本项目已配置了基于OpenCode的AI代码审查工作流，使用GLM4.6模型进行自动代码审查。

## 工作流功能

- 当创建或更新Pull Request时自动触发代码审查
- 支持在PR或Issue中使用 `/opencode` 或 `/oc` 命令手动触发AI审查
- 支持对特定代码行进行评论并使用 `/opencode` 或 `/oc` 进行针对性分析

## 配置步骤

### 1. 设置API密钥

在GitHub仓库中设置智谱AI的API密钥：

1. 进入仓库的 `Settings` > `Secrets and variables` > `Actions`
2. 点击 `New repository secret`
3. 添加名为 `ZHIPUAI_API_KEY` 的密钥，值为你的智谱AI API密钥

如果你还没有智谱AI的API密钥，请访问 [智谱AI开放平台](https://open.bigmodel.cn/) 获取。

### 2. 确保工作流权限

确保GitHub Actions有足够的权限运行工作流：

1. 进入仓库的 `Settings` > `Actions` > `General`
2. 在 "Workflow permissions" 部分选择 "Read and write permissions"
3. 勾选 "Allow GitHub Actions to create and approve pull requests"

## 使用方法

### 自动审查

创建Pull Request时，工作流会自动触发并对代码进行审查。

### 手动触发

在Pull Request或Issue评论中使用以下命令：

```
/opencode 请检查这段代码的性能
/oc 分析这个函数的逻辑问题
```

### 代码行特定审查

在Pull Request的Files标签页中对特定代码行添加评论：

```
/opencode 分析这里的潜在bug
/oc 请优化这段代码的性能
```

## 自定义审查规则

你可以通过修改 `.github/workflows/ai-review.yml` 文件中的 `prompt` 部分来自定义代码审查的重点和标准。

## 故障排除

如果工作流无法正常运行，请检查：

1. API密钥是否正确设置
2. GitHub Actions权限是否足够
3. 工作流文件语法是否正确

更多信息请参考 [OpenCode GitHub文档](https://opencode.ai/docs/zh-cn/github/)