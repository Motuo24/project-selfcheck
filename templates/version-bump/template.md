# 版本号变更模板

## 用途

用于版本号决策与同步的标准化流程。适用于提交前自查场景。

## 使用边界

- 适用：提交前需要决策版本号
- 不适用：无版本号管理的项目

## 数据形状

```json
{
  "current_version": "当前版本号",
  "change_type": "feature / fix / optimize",
  "suggested_version": "建议版本号",
  "build_number_source": "git / manual",
  "files_to_sync": ["需要同步版本号的文件列表"],
  "changelog_entry": "更新日志条目"
}
```

## 视觉/交互限制

- 使用 AskUserQuestion 与用户交互
- 每次只处理一个议题
- 等待用户确认后再修改文件

## 边界情况

- 无 Git 仓库：build 号需要用户手动指定
- 无前端展示：跳过文件同步步骤
- 无更新日志：跳过 changelog 步骤
