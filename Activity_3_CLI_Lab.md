# CC 101 Laboratory Activity: Exploring the Windows Command Line

**Republic of the Philippines**
**Sorsogon State University**
**College of Information and Communications Technology – Bulan Campus**
Zone 8, Bulan, Sorsogon | Tel. No.: 056 311-0103 | Email: cict@sorsu.edu.ph

## Command Line Exploration Documentation

- **Name:** Julius B. Banalnal
- **Student ID:** 26128352
- **Section:** BSCS 1-1
- **Date Performed:** 09/23/2026
- **Instructor:** John Mark Gabrentina

| Item | Details |
|---|---|
| Course | CC 101 Introduction to Computing (BSCS 1st Year) |
| Course Outcome | CO2: Identify the functions and relationships of major hardware and software components |
| Output | Command Line Exploration Documentation (PDF) |
| Estimated time | 2 to 2½ hours |
| Reference | CC 101 Lecture Notes: Exploring the Windows Command Line |

---

## Instructions

Follow every step in order, take the screenshots marked **[Screenshot]**, and answer the questions marked **[Answer]** in your documentation.

**Before you start**

- You need a Windows 10 or 11 computer. No administrator rights are needed.
- To take a screenshot, press **Windows + Shift + S**, drag over the terminal window, then paste it (Ctrl + V) into your documentation.
- Replace the sample values (Julius B. Banalnal, BSCS 1-1) with **your own** details.
- Type every command yourself. Do not copy and paste; typing is how you learn.

## Introduction

The command line is a text-based way of controlling a computer by entering commands instead of mainly using menus and windows. In this activity, I practiced using Command Prompt and PowerShell to inspect the computer, create folders and files, manage files, and read system information. I also learned how commands can be combined and how PowerShell can perform simple number conversions. The activity helped me understand that the command line can be useful for doing computer tasks quickly and directly.

---

## Part A: Open the Two Shells

1. Press Windows + R, type `cmd`, and press Enter. Type `cls` and press Enter.
2. Type `echo Julius B. Banalnal, BSCS 1-1` (your own name and section) and press Enter. **[Screenshot] Figure A1**

   ![Figure A1. Command Prompt showing the student's name and section.](images/figure-A1.png)

   *Figure A1. Command Prompt showing the student's name and section.*

3. Press Windows + R, type `powershell`, and press Enter. Type the same echo command, but put the text in quotation marks: `echo "Julius B. Banalnal, BSCS 1-1"`. PowerShell treats the comma as a list separator without them. **[Screenshot] Figure A2**

   ![Figure A2. PowerShell showing the student's name and section.](images/figure-A2.png)

   *Figure A2. PowerShell showing the student's name and section.*

**[Answer] A-Q1.** Compare the two prompts. What is different, and what does each part of the Command Prompt prompt mean?

**Answer:** The Command Prompt prompt is shown as `C:\Users\Administrator>`. The `C:` part is the drive, `Users\Administrator` is the current folder path, and the `>` symbol shows that the command line is ready for me to type a command. PowerShell uses a similar path but adds `PS` at the beginning, such as `PS C:\Users\Administrator>`.

---

## Part B: Inspect Your System (Command Prompt)

Use the Command Prompt window for Parts B to D.

1. Run these commands one at a time: `whoami`, then `hostname`, then `ver`. **[Screenshot] Figure B1**

   ![Figure B1. whoami, hostname, and ver results.](images/figure-B1.png)

   *Figure B1. whoami, hostname, and ver results.*

2. Run the command below. It may take 10 to 30 seconds. **[Screenshot] Figure B2**

   ```cmd
   systeminfo | findstr /B /C:"OS Name" /C:"OS Version" /C:"System Type" /C:"Total Physical Memory"
   ```

   ![Figure B2. systeminfo/findstr command and the following Command Prompt activity.](images/figure-B2.png)

   *Figure B2. systeminfo/findstr command and the following Command Prompt activity.*

3. Run `ipconfig`. Find the adapter that shows an IPv4 Address. **[Screenshot] Figure B3**

   ![Figure B3. IPv4 address shown by ipconfig.](images/figure-B3.png)

   *Figure B3. IPv4 address shown by ipconfig.*

**[Answer] B-Q1.** Complete this table in your documentation using your results:

| Item | Your result |
|---|---|
| Logged-in account (whoami) | pc-31\administrator |
| Computer name (hostname) | PC-31 |
| OS name | Windows 10 |
| OS version | 10.0.19045.3633 |
| System type (x64 or ARM) | x64-based PC |
| Total physical memory (RAM) | 15,675 |
| IPv4 address | 192.168.88.231 |

**[Answer] B-Q2.** The `|` symbol in step 2 is called a **pipe**. Run `systeminfo` alone and compare. In your own words, what did `| findstr` do?

**Answer:** The pipe sends the output from `systeminfo` to `findstr`. Instead of showing the whole `systeminfo` report, `findstr` searches the output and keeps only the lines that match the OS name, OS version, system type, and total physical memory terms.

---

## Part C: Build a Folder Structure

1. Go to your user folder and create the lab folders:

   ```cmd
   cd %USERPROFILE%
   mkdir CC101-Lab
   cd CC101-Lab
   mkdir Notes Projects Screenshots
   ```

2. Create a text file about yourself (use your own details):

   ```cmd
   echo Name: Julius B. Banalnal > profile.txt
   echo Section: BSCS 1-1 >> profile.txt
   echo Favorite app: YouTube >> profile.txt
   type profile.txt
   ```

   **[Screenshot] Figure C1** (show all commands and the output of `type`)

   ![Figure C1. CC101-Lab folder creation and profile.txt commands.](images/figure-C1.png)

   *Figure C1. CC101-Lab folder creation and profile.txt commands.*

3. Run `tree /F` to display your folder structure. **[Screenshot] Figure C2**

   ![Figure C2. Folder structure displayed by tree /F.](images/figure-C2.png)

   *Figure C2. Folder structure displayed by tree /F.*

4. Open File Explorer, go to `C:\Users\(your account)\CC101-Lab`, and open `profile.txt` in Notepad. **[Screenshot] Figure C3** (File Explorer and Notepad side by side)

   ![Figure C3. Profile and lab-folder activity captured in the supplied screenshot set.](images/figure-C3.png)

   *Figure C3. Profile and lab-folder activity captured in the supplied screenshot set.*

**[Answer] C-Q1.** What would happen if you used `>` instead of `>>` in the second echo line? Test it on a new file (`test.txt`) and explain.

**Answer:** Using `>` instead of `>>` would overwrite the file contents each time. In the second echo line, the Section line would replace what was already in the file instead of being added after the Name line. The `>>` operator is used to append new text.

---

## Part D: Copy, Rename, and Delete Files

```cmd
copy profile.txt Notes\profile-copy.txt
cd Notes
ren profile-copy.txt about-me.txt
echo This file will be deleted > temp.txt
dir
del temp.txt
dir
cd ..
tree /F
```

**[Screenshot] Figure D1** (from `copy` to the first `dir`) and **[Screenshot] Figure D2** (from `del` to `tree /F`)

![Figure D1. Copy, rename, and directory operations.](images/figure-D1.png)

*Figure D1. Copy, rename, and directory operations.*

![Figure D2. Delete operation and resulting folder tree.](images/figure-D2.png)

*Figure D2. Delete operation and resulting folder tree.*

**[Answer] D-Q1.** After `del temp.txt`, check your Recycle Bin. Is `temp.txt` there? What does this tell you about deleting files from the command line?

**Answer:** No, `temp.txt` does not go to the Recycle Bin when it is deleted with `del` in Command Prompt. The command-line `del` command removes the file directly instead of sending it through the normal Recycle Bin process. This means I should be careful when using `del` because recovery is not as simple as restoring a file from the Recycle Bin.

---

## Part E: Explore PowerShell

Switch to the PowerShell window.

1. Go to your lab folder and list and read its files:

   ```powershell
   cd $HOME\CC101-Lab
   Get-ChildItem
   Get-Content profile.txt
   $PSVersionTable
   ```

   **[Screenshot] Figure E1**

   ![Figure E1. PowerShell listing, profile contents, and version information.](images/figure-E1.png)

   *Figure E1. PowerShell listing, profile contents, and version information.*

2. Run `Get-Help Get-ChildItem`. If PowerShell asks whether to run Update-Help, type `N` and press Enter. **[Screenshot] Figure E2**

   ![Figure E2. PowerShell help output.](images/figure-E2.png)

   *Figure E2. PowerShell help output.*

   ![Figure E2 (continued). PowerShell help output.](images/figure-E2-continued.png)

   *Figure E2 (continued). PowerShell help output.*

3. Take the **last three digits of your student ID number** (for example, 2026-128352 → 352). Convert it with PowerShell:

   ```powershell
   [Convert]::ToString(352, 2)
   [Convert]::ToString(352, 8)
   '{0:X}' -f 352
   ```

   **[Screenshot] Figure E3**

   ![Figure E3. Number conversion of 352 in PowerShell.](images/figure-E3.png)

   *Figure E3. Number conversion of 352 in PowerShell.*

**[Answer] E-Q1.** Write your number in decimal, binary, octal, and hexadecimal. Keep this; you will verify it by hand in Week 5.

**Answer:** Decimal: 352. Binary: 101100000. Octal: 540. Hexadecimal: 160.

---

## Part F: Discover a New Command

1. In Command Prompt, type `help` to see a list of commands.
2. Choose **one** command that was **not** taught in this lesson and is safe to run (for example: `date /t`, `time /t`, `tasklist`, `vol`, or `color 0A`).
3. Read its help with `command /?` (for example, `tasklist /?`), then run it. **[Screenshot] Figure F1** (help output) and **[Screenshot] Figure F2** (command result)

   ![Figure F1. Help output captured in the supplied screenshot set.](images/figure-F1.png)

   *Figure F1. Help output captured in the supplied screenshot set.*

   ![Figure F2. date /t command result showing 09/23/2026.](images/figure-F2.png)

   *Figure F2. `date /t` command result showing 09/23/2026.*

**[Answer] F-Q1.** What does your chosen command do, and when would it be useful?

**Answer:** The command I used was `date /t`. It displays the current system date directly in Command Prompt without opening the Date and Time settings. It is useful when I need to quickly check the computer's current date while working in the command line.

---

## Part G: Reflection

**[Answer]** Answer in 3 to 5 sentences each:

**G-Q1.** Which task in this activity was faster in the CLI than in the GUI? Which was easier in the GUI? Explain why.

**Answer:** Creating folders and files with commands such as `mkdir` and `echo` was faster in the CLI because I could type the commands directly without opening several windows. Opening and checking a file was easier in the GUI because I could see the folders and files visually. The GUI felt more convenient for browsing, while the CLI was faster for repeated file operations.

**G-Q2.** What error did you encounter (if any), what caused it, and how did you fix it?

**Answer:** I encountered an error during the first PowerShell number conversion. I typed the conversion command incorrectly and PowerShell reported an unexpected token error. I fixed it by using the correct `[Convert]::ToString` syntax, and the conversion then worked.

**G-Q3.** Give one real-world job or situation in computing where knowing the command line would be important.

**Answer:** Knowing the command line is important in IT support and system administration. Technicians can use commands to check computers, manage files, inspect network information, and troubleshoot problems. It is also useful when working with many computers because some tasks can be done faster through commands.

---

## Documentation and Submission

Submit one PDF that records what you did, what the computer showed, and what you learned. Someone reading it should be able to repeat your work.

### Required Contents (in this order)

1. **Cover page:** activity title, your full name, student ID, section, date performed, and instructor's name.
2. **Introduction** (3 to 5 sentences): what the command line is and the purpose of this activity, in your own words.
3. **Procedure and results, Parts A to F:** for each part, a short heading, the commands you typed, the labeled screenshots, and your answers to that part's [Answer] questions.
4. **Commands learned table:** every command you used and what it does, in your own words.
5. **Reflection:** your answers to G-Q1 to G-Q3.

### Formatting Rules

| Item | Requirement |
|---|---|
| File type | PDF (write in Word or Google Docs, then export as PDF) |
| File name | CC101_CLI-Lab_Banalnal_Julius.pdf |
| Font | Arial or Calibri, 11 pt; commands in Consolas or Courier New |
| Screenshots | Crop to the terminal window; text must be readable. Label each one below the image, e.g., "Figure B2. Filtered systeminfo output" |
| Personal details | Your own name, section, and student ID must appear in Figures A1, C1, and E3 |
| Total screenshots | 16 (A1–A2, B1–B3, C1–C3, D1–D2, E1–E3, F1–F2) |

### Commands Learned Table

| Command | Shell | What it does |
|---|---|---|
| `cmd` | Run dialog | Opens Command Prompt |
| `cls` | Command Prompt | Clears the Command Prompt screen |
| `echo` | Command Prompt | Displays text or writes text into a file |
| `powershell` | Run dialog | Opens PowerShell |
| `whoami` | Command Prompt | Shows the current logged-in account |
| `hostname` | Command Prompt | Shows the computer name |
| `ver` | Command Prompt | Shows the Windows version |
| `systeminfo` | Command Prompt | Displays detailed system information |
| `findstr` | Command Prompt | Finds matching text in command output |
| `\|` | Command Prompt | Pipes output from one command into another |
| `ipconfig` | Command Prompt | Shows network configuration such as IPv4 |
| `cd` | Command Prompt / PowerShell | Changes the current folder |
| `mkdir` | Command Prompt | Creates a new folder |
| `>` | Command Prompt | Creates or overwrites a file with redirected output |
| `>>` | Command Prompt | Appends redirected output to a file |
| `type` | Command Prompt | Displays a text file's contents |
| `tree /F` | Command Prompt | Shows folders and files in a tree |
| `copy` | Command Prompt | Copies a file to another location |
| `ren` | Command Prompt | Renames a file |
| `dir` | Command Prompt | Lists files and folders |
| `del` | Command Prompt | Deletes a file from the command line |
| `Get-ChildItem` | PowerShell | Lists items in the current location |
| `Get-Content` | PowerShell | Displays the contents of a file |
| `$PSVersionTable` | PowerShell | Shows PowerShell version information |
| `Get-Help` | PowerShell | Displays help information for commands |
| `[Convert]::ToString` | PowerShell | Converts a number to another base |
| `'{0:X}' -f` | PowerShell | Formats a number as hexadecimal |
| `help` | Command Prompt / PowerShell | Displays help information |
| `date /t` | Command Prompt | Displays the current system date |

### Submission

- Upload the PDF to the activity page in the course LMS before the deadline your instructor sets.
- Outputs must be your own work. Identical screenshots or answers will be treated as plagiarism under the class policy.
- Keep your `CC101-Lab` folder; later activities may build on it.

### Grading Rubric

The documentation is scored out of 100 points and counts under Laboratory: Project.

| Criterion | Points | Full marks | Partial marks | Low marks |
|---|---|---|---|---|
| Completeness of procedure | 30 | All 16 labeled, readable screenshots; every part A to F documented | 1 to 4 screenshots missing or unreadable | 5 or more screenshots missing |
| Accuracy of results | 20 | System-information table complete; commands and conversions correct and personalized | Minor errors or 1 to 2 missing values | Many errors, or results not the student's own |
| Answers to guide questions (A to F) | 20 | Correct, clear, in the student's own words | Mostly correct but brief or vague | Missing, incorrect, or copied |
| Reflection (G-Q1 to G-Q3) | 15 | Specific, honest, and linked to the activity | General statements with few specifics | Missing or off-topic |
| Organization and formatting | 15 | Follows the required order, naming, and formatting rules; commands learned table complete | Some rules not followed | Disorganized; wrong file type or name |
| **Total** | **100** | | | |
