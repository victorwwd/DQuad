# DQuad - Windows 四象限文件管理器

一款自用极简轻量级 Windows 文件管理器，采用四象限布局，支持多标签页和书签管理。

- 持续完善中...

<img width="1186" height="793" alt="DQuad" src="https://github.com/user-attachments/assets/da6dd44a-1853-43d7-85b8-86047badd2c7" />


## 功能特性

- **四象限布局**：同时浏览四个目录，提高工作效率
- **多标签页**：每个象限独立标签页，支持新建/关闭/切换
- **书签管理**：支持分组、拖拽排序、导入/导出
- **面包屑导航**：快速跳转到任意父目录
- **文件操作**：复制、剪切、粘贴、删除、重命名
- **系统集成**：右键菜单支持系统原生操作
- **状态持久化**：自动保存窗口布局和标签页状态

## 快捷键

| 按键 | 功能 |
|------|------|
| `Ctrl+T` | 新建标签页 |
| `Ctrl+W` | 关闭标签页 |
| `Ctrl+D` | 添加当前路径到书签 |
| `Ctrl+C/X/V` | 复制/剪切/粘贴 |
| `F2` | 重命名 |
| `F5` | 刷新 |
| `Del` | 删除 |

## 编译

需要 MinGW-w64 或 MSVC：

```bash
gcc main.c -o DQuad.exe -std=c11 -mwindows -lcomctl32 -lole32 -luuid -lshlwapi -DUNICODE -D_UNICODE
```

## 配置文件

- `bookmarks.ini` - 书签配置
- `state.ini` - 窗口状态

## 许可证

MPL 2.0 License
