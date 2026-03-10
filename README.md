# 📘 RHCSA Notes

## 👥 User Monitoring Commands

- **who**

Shows **users currently logged into the system**.  
Displays:  
* Username  
* Terminal used  
* Login time  
* Remote IP (if applicable)

- **w**

Shows **logged-in users and what they are currently doing**.

Displays:  
* Active users   
* Running commands    
* System load information

## 🖥️ Virtual Terminal Command

- **chvt**

Used to **switch between virtual terminals (TTYs)**.

Example:

```
sudo chvt 2
```

Switches to **virtual terminal 2 (`tty2`)**.

## 📖 Manual Pages (Documentation)

- **man**

Used to **view detailed documentation of Linux commands**.

#### Important Facts About `man`

* All manual pages are indexed in the **mandb database**.
* This database allows quick searching of documentation.

---

#### Search Man Pages

```
man -k keyword
```
Example:

```
man -k password
```

Searches commands related to **password**.

## 📝 Vim Editor Commands

### Modes in Vim

Vim works in different modes:

1. **Command Mode** – default mode for navigation and commands
2. **Insert Mode** – used to write text
3. **Visual Mode** – used to select text

---

### Basic Mode Commands

| Command | Function                                    |
| ------- | ------------------------------------------- |
| `Esc`   | Enter command mode                          |
| `i`     | Enter insert mode before cursor             |
| `a`     | Enter insert mode after cursor              |
| `o`     | Open a new line below and enter insert mode |

---

### File Saving & Exit

| Command | Function            |
| ------- | ------------------- |
| `:wq`   | Save and quit       |
| `:q`    | Quit                |
| `:q!`   | Quit without saving |

---

### Editing Commands

| Command    | Function                   |
| ---------- | -------------------------- |
| `dd`       | Delete current line        |
| `yy`       | Copy current line          |
| `p`        | Paste copied text          |
| `u`        | Undo last operation        |
| `Ctrl + r` | Redo last undone operation |

---

### Navigation Commands

| Command | Function              |
| ------- | --------------------- |
| `gg`    | Go to top of file     |
| `G`     | Go to end of file     |
| `^`     | Move to start of line |
| `$`     | Move to end of line   |
| `w`     | Move to next word     |

---

### Searching in Vim

| Command | Function                   |
| ------- | -------------------------- |
| `/text` | Search forward for "text"  |
| `?text` | Search backward for "text" |

---

### Replace Text

Replace all occurrences of a word in the file:

```
:%s/old/new/g
```
