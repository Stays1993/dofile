# 使用`chezmoi`管理Linux配置文件
## 1. 安装`chezmoi`

```bash
sh -c "$(curl -fsLS https://chezmoi.io/get)"
```

验证安装：

```bash
chezmoi --version
```

## 2. 初始化`chezmoi`
初始化 Chezmoi，它会创建一个 ~/.local/share/chezmoi 目录来存储你的配置文件：

```bash
chezmoi init
```

## 3. 添加配置文件
将你的配置文件添加到 Chezmoi 管理中。例如：

```bash
# 添加 Zsh 配置文件
chezmoi add ~/.zshrc

# 添加 Starship 配置文件
chezmoi add ~/.config/starship.toml

# 添加 Neovim 配置文件
chezmoi add ~/.config/nvim/init.lua
```

Chezmoi 会将这些文件复制到 `~/.local/share/chezmoi` 目录中，并生成对应的管理文件。

## 4. 编辑配置文件
你可以直接编辑 Chezmoi 管理的文件，而不是原始文件。例如：

```bash
chezmoi edit ~/.zshrc
```

这会打开 `~/.local/share/chezmoi/dot_zshrc` 文件供你编辑。

## 5. 应用配置
将 Chezmoi 管理的配置文件应用到你的系统中：

```bash
chezmoi apply
```

Chezmoi 会自动创建符号链接或将文件复制到正确的位置。

## 6. 备份到 Git
Chezmoi 支持与 Git 集成，方便你备份和同步配置文件。

1. 初始化 Git 仓库：

```bash
chezmoi cd
git init
git add .
git commit -m "Initial commit"
```

2. 推送到远程仓库（如 GitHub）：

```bash
git remote add origin https://github.com/你的用户名/你的仓库名.git
git branch -M main
git push -u origin main
```

## 7. 在新系统上恢复配置
在新系统上，你可以通过 Chezmoi 快速恢复你的配置文件：

1. 安装 Chezmoi（参考步骤 1）。
2. 从远程仓库初始化 Chezmoi：

```bash
chezmoi init https://github.com/你的用户名/你的仓库名.git
```
3. 应用配置：

```bash
chezmoi apply
```

## 8. 常用命令

| 命令 | 说明 |
| ---- | ---- |
| `chezmoi add <文件>` | 添加文件到 Chezmoi 管理 |
| `chezmoi edit <文件>` | 编辑 Chezmoi 管理的文件 |
| `chezmoi apply` | 应用 Chezmoi 管理的配置 |
| `chezmoi diff` | 查看 Chezmoi 管理的文件与系统的差异 |
| `chezmoi cd` | 进入 Chezmoi 的管理目录 |
| `chezmoi init <Git 仓库>` | 从 Git 仓库初始化 Chezmoi |
| `chezmoi update` | 从 Git 仓库更新 Chezmoi 管理的配置 |

## 9. 示例工作流
1. 在现有系统上初始化 Chezmoi 并添加配置文件：

```bash
chezmoi init
chezmoi add ~/.zshrc
chezmoi add ~/.config/starship.toml
chezmoi add ~/.config/nvim/init.lua
```

2. 将配置备份到 GitHub：

```bash
chezmoi cd
git init
git add .
git commit -m "备份配置文件"
git remote add origin https://github.com/Stays1993/dofile.git
git push -u origin main
```

3. 在新系统上恢复配置：

```bash
chezmoi init https://github.com/Stays1993/dofile.git
chezmoi apply
```

通过以上步骤，你可以轻松使用 Chezmoi 备份和管理你的配置文件。

## 10. 安装[`zplug`](https://github.com/zplug/zplug?tab=readme-ov-file)
```bash
curl -sL --proto-redir -all,https https://raw.githubusercontent.com/zplug/installer/master/installer.zsh | zsh
```

## 11. 安装[`starship`](https://github.com/starship/starship)
```bash
curl -sS https://starship.rs/install.sh | sh
```

