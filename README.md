# 📘 RHCSA Notes

## 👥 User Monitoring Commands

### who

Shows **users currently logged into the system**.  
Displays:  
* Username  
* Terminal used  
* Login time  
* Remote IP (if applicable)

### w

Shows **logged-in users and what they are currently doing**.

Displays:  
* Active users   
* Running commands    
* System load information

## 🖥️ Virtual Terminal Command

### chvt

Used to **switch between virtual terminals (TTYs)**.

**Example:**

```
sudo chvt 2
```

Switches to **virtual terminal 2 (`tty2`)**.

## 📖 Manual Pages (Documentation)

### man

Used to **view detailed documentation of Linux commands**.

#### Important Facts About `man`

* All manual pages are indexed in the **mandb database**.
* This database allows quick searching of documentation.

---

#### Search Man Pages

```
man -k keyword
```
**Example:**
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

## 🔄 Understanding Redirection

Redirection allows you to **control where command input and output go** by using Linux standard streams.

Linux commands use three standard streams:

| Stream         | Name            | Description           |
| -------------- | --------------- | --------------------- |
| **STDIN (0)**  | Standard Input  | Input to a command    |
| **STDOUT (1)** | Standard Output | Normal command output |
| **STDERR (2)** | Standard Error  | Error messages        |

Redirection helps send output to files, suppress errors, or provide input from files.

### 1. < (Input Redirection)

Takes input from a file instead of keyboard input.

**Example:** `sort < names.txt`

Sort reads input from names.txt.

### 2. > (Overwrite Output)

Redirects command output to a file. If the file exists, it **overwrites** it.

**Example:** `ls > files.txt`

The output of `ls` is saved in **files.txt**.

### 3. >> (Append Output)

Appends command output to the end of a file.

**Example:** `date >> log.txt`

The date is added to **log.txt** without deleting existing content.

### 4. 2>/dev/null (Discard Errors)

Redirects error messages to `/dev/null`, which discards them.

**Example:**
```
find / -name test
```

**What this does:**

Searches the entire filesystem (/) for files named test. But many directories are restricted. So you may see many errors like:  

*find: ‘/root’: Permission denied or find: ‘/proc/1234’: Permission denied*

These messages come from STDERR (error output).

Using 2>/dev/null:   
```
fin1d / -name test 2>/dev/null`
```
**Meaning:**

- 2 → STDERR
- > → redirect
- dev/null → discard output


So the command becomes:

Send all error messages to /dev/null, which discards them.

**Result:**

- Only valid results appear  
- Permission errors disappear

`/dev/null` is often called the **black hole of Linux**.

## 🔗 Understanding Pipes

### `|` (Pipe)

A pipe sends the **output of one command as input to another command**.

**Example:** 
```
ps aux | grep ssh
```
Shows processes related to **ssh**.

## Repeating commands from History
- Using arroy key.
- `Ctrl + r`: used when you remember part of the command but not the full command.  
- `!number`: repeats commands from history based on its number.    
- `!a`: repeats last command that start with `a`.

## Keyboard shortcuts
- `Ctrl a`: moves cursor to the start of the current line.   
- `Ctrl e`: moves cursor to the end of the current line.   
- `Ctrl l`: clear the screen.     
- `Ctrl d`: deletes next word.   
- `Ctrl u`: removes the current line.   
- `Alt b`: moves cursor one word backword.   
- `Alt f`: moves cursor one word forward.   

## Shell expansion
- `ls`: Lists files and directories in the current directory.   
- `ls -l`: Displays files in long listing format.    
- `ls *`: Displays contents of directories as well.    
- `ls -d *`: The -d option tells ls to show directory names instead of their contents.   
- `ls -d /etc/*`: Lists all files and directories inside /etc.   
- `ls -d /etc/a*`: Lists files in /etc that start with letter a.   
- `ls -d /etc/a????*`: This command lists files starting with a + at least four characters.   
- `ls -d /etc/[a-d]*`: Lists file that start with any letter from a to d.   
- `which passwd`: Shows the location of a command executable.   

## Alias
An alias is a shortcut for a command in Linux. It allows you to create a short or custom command that executes a longer command.

### Temporary vs Permanent Alias
**Temporary Alias**

If you create an alias in the terminal:
```
alias ll='ls -l'
```
It works only in the current session.Once you close the terminal, it disappears.

**Permanent Alias**

To make aliases permanent, add them to: `~/.bashrc`

**Example:**
```
vim ~/.bashrc
```
**Add:**

alias ll='ls -l'  
alias update='sudo dnf update'

**Then reload:**  
```
source ~/.bashrc
```
Now the alias works every time you open the terminal.

### Removing an Alias

To remove an alias:
```
unalias name
```            
