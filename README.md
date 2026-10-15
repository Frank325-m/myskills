# myskills

个人 Trae 技能库，积累自己使用的各类技能，便于快速使用、更新与维护。

## 目录结构

```
myskills/
├── README.md            # 仓库说明：结构、约定、使用流程、技能索引
├── LICENSE              # Apache 2.0
└── skills/              # 技能库本体：每个技能一个目录，扁平存放
    └── _template/       # 新技能模板（"_" 开头 = 辅助目录，不是技能）
        └── SKILL.md
```

- **扁平存放**：所有技能直接放在 `skills/<技能名>/` 下，不按分类建子目录。Trae 按一级目录扫描技能，扁平结构一条命令即可完成安装；技能多了以后靠下方索引表做逻辑检索。
- **`_` 开头目录**：仓库辅助内容（如 `_template`），不是技能，安装时跳过。

## 快速上手

### 新建技能

```bash
cp -R skills/_template skills/<新技能名>   # 如 skills/my-skill
```

然后编辑 `SKILL.md`：改写 frontmatter 的 `name`（与目录名一致）和 `description`，再填充正文各章节。

### 安装到 Trae（全局）

```bash
# 安装单个技能
cp -R skills/<技能名> ~/.trae-cn/skills/

# 全量安装（自动跳过 "_" 开头的辅助目录）
rsync -av --exclude='_*' skills/ ~/.trae-cn/skills/
```

安装后重启 Trae 或新开会话即可使用。

### 更新技能

```bash
# 1. 在仓库内修改技能内容
# 2. 重新执行安装命令覆盖（单个技能）
cp -R skills/<技能名> ~/.trae-cn/skills/
# 3. 提交变更
git add skills/<技能名> && git commit
```

### 移除技能

```bash
rm -rf skills/<技能名>                    # 删仓库目录
rm -rf ~/.trae-cn/skills/<技能名>         # 删 Trae 安装目录
```

## 维护约定

- 技能目录命名使用 **kebab-case**（如 `git-commit`），与 frontmatter `name` 一致；
- `SKILL.md` 必需，frontmatter 必含 `name`、`description`，description 写明**功能 + 触发时机**，控制在 200 字符内；
- 辅助资源放在技能目录内的子目录：`scripts/`（脚本）、`references/`（参考文档）、`assets/`（素材）；
- `_` 开头目录为仓库辅助目录，不是技能，安装时跳过；
- git 提交遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/)。

## 技能索引

| 技能名 | 说明 | 添加时间 |
|--------|------|----------|
| resume-screening | 简历定向筛查：输入简历+岗位名称，叠加在线教育3岗位（AI应用工程师/大数据工程师/高级运维工程师）硬性门槛与专项校验，输出定向筛查结论 | 2026-10-15 |

<!-- 新增技能后在此登记一行 -->
