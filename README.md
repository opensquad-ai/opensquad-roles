# opensquad-roles

OpenSquad 角色商店仓库，包含可一键安装的角色卡（Role Cards）。

## 目录结构

```
opensquad-roles/
├── index.json               # 角色索引，商店从此读取列表
├── likes.json               # 点赞数据（由系统自动维护）

```

## index.json 字段说明

| 字段 | 说明 |
|---|---|
| `id` | 角色唯一标识符（与 .md 文件名一致） |
| `name` | 角色显示名称 |
| `description` | 简短描述 |
| `category` | 分类（dev / pm / ops / support / writing / analyst） |
| `tags` | 标签列表 |
| `author` | 作者 |
| `version` | 版本号 |
| `download_url` | zip 文件的 raw.githubusercontent.com 下载地址 |

## 角色卡格式

```markdown
---
name: 角色名称
description: 简短描述
category: dev
tags: [tag1, tag2]
---

## 角色定义

（角色提示词正文）
```

## 安装行为

商店安装时会将 zip 内的 `{role_id}.md` 提取并写入项目根目录的 `role_cards/{role_id}.md`。

## 贡献角色卡

1. 新建 `{role_id}.md` 文件，填写 YAML frontmatter 和角色正文
2. 在 `index.json` 中追加条目
3. 运行 `python ../build_zips.py` 生成 zip
4. 提交 PR
