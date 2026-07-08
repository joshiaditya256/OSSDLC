# CDAC Operating Systems Lab – Practical Notes

Covers three parts: **Linux**, **Git**, **Docker**.
Practiced on Ubuntu VM (VirtualBox). Git commands also work in Git Bash on Windows.

---

## Table of Contents
1. [Linux Practical](#linux-practical)
2. [Git Practical](#git-practical)
3. [Docker Practical](#docker-practical)
4. [Quick Reference – Most Important Commands](#quick-reference)

---

## Linux Practical

### 1. Start Ubuntu
- Open Oracle VirtualBox → select VM → Start → login.

### 2. Open Terminal
```
Ctrl + Alt + T
```

### 3. Check Current Location
```bash
pwd
ls
ls -l      # detailed view
ls -a      # hidden files
```

### 4. Create Directory
```bash
mkdir CDAC
ls
cd CDAC
pwd
```

### 5. Create Multiple / Nested Directories
```bash
mkdir Linux Git Docker
mkdir -p Project/src/java
ls
```

### 6. Create Files
```bash
touch file1.txt
touch file2.txt file3.txt
ls
```

### 7. Create File with Data
```bash
cat > student.txt
```
Type:
```
Name: ABC
Course: PG-DAC
Operating System Lab
```
Press `Ctrl + D` to save.

### 8. Display File
```bash
cat student.txt
less student.txt   # press q to quit
```

### 9. Copy Files
```bash
cp student.txt copy.txt
cp student.txt Linux/
ls
```

### 10. Move and Rename
```bash
mv copy.txt newcopy.txt
mv newcopy.txt Git/
ls
```

### 11. Find Files
```bash
find . -name "*.txt"
find . -name student.txt
```

### 12. Search Text Using grep
```bash
grep Operating student.txt
grep -i operating student.txt   # ignore case
grep -n Operating student.txt   # show line numbers
```

### 13. Append Data
```bash
echo "Linux Commands" >> student.txt
cat student.txt
```

### 14. Count
```bash
wc student.txt
wc -l student.txt   # lines
wc -w student.txt   # words
wc -c student.txt   # characters
```

### 15. Head and Tail
```bash
head student.txt
tail student.txt
```

### 16. Sort
```bash
sort student.txt
```

### 17. Redirect Output
```bash
ls > list.txt
ls >> list.txt   # append
cat list.txt
```

### 18. Pipe
```bash
ls | wc -l
cat student.txt | grep Linux
```

### 19. Permissions
```bash
ls -l
chmod 777 student.txt
ls -l
```

### 20. User Commands
```bash
whoami
id
sudo useradd student1
sudo passwd student1
su student1
exit
sudo userdel student1
sudo userdel -r student1   # delete with home directory
```
> ⚠️ Needs sudo privileges on the VM.

### 21. Delete Files
```bash
rm file2.txt
rmdir Docker        # empty directory only
rm -r Linux          # non-empty directory
```

### 22. System Information
```bash
date
cal
free -h
df -h
hostname
```

### 23. Running Processes
```bash
ps
ps -ef
kill PID   # replace PID with actual process ID
```

### 24. Hidden File
```bash
touch .hidden
ls -a
```

### 25. Archive
```bash
tar -cvf project.tar Project
tar -xvf project.tar
```

### 26. Zip
```bash
zip files.zip student.txt
unzip files.zip
```
> ⚠️ If `zip`/`unzip` not found: `sudo apt install zip unzip`

---

## Git Practical

### 1. Open Ubuntu & Terminal
Same as Linux Step 1–2 above.

### 2. Check Git Installation
```bash
git --version
# if not installed:
sudo apt update
sudo apt install git
git --version
```

### 3. Configure Git (First Time Only)
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list
```
> ℹ️ This sets your **commit identity**, not a GitHub account login.
> In the exam, run `git config --list` first — if already set, skip this step.

### 4. Create Project Folder
```bash
mkdir GitLab
cd GitLab
pwd
```

### 5. Initialize Git Repository
```bash
git init
git status
```

### 6. Create Files
```bash
touch file1.txt
touch file2.txt file3.txt
ls
```

### 7. Add Content
```bash
cat > file1.txt
```
Type:
```
Hello CDAC
Git Practical
```
`Ctrl + D` to save, then:
```bash
cat file1.txt
```

### 8. Check Status
```bash
git status
```

### 9. Add Files (Staging)
```bash
git add file1.txt
git add .
git status
```

### 10. Commit
```bash
git commit -m "First Commit"
git status
```

### 11. View Commit History
```bash
git log
git log --oneline
```

### 12–13. Modify & Commit Again
```bash
echo "Second Line" >> file1.txt
cat file1.txt
git status
git add .
git commit -m "Updated file1"
git log --oneline
```

### 14. Create Branch
```bash
git branch
git branch feature
git branch
```

### 15. Switch Branch
```bash
git checkout feature
# or
git switch feature
git branch
```

### 16. Modify File in Branch
```bash
echo "Feature Branch Data" >> file1.txt
cat file1.txt
git add .
git commit -m "Feature Branch Update"
```

### 17. Switch Back
```bash
git checkout master
# or (check with `git branch` which name your repo uses)
git checkout main
```

### 18. Merge Branch
```bash
git merge feature
cat file1.txt
git log --oneline
```

### 19. Delete Branch
```bash
git branch -d feature
git branch
```

### 20. Clone Repository (Local)
```bash
cd ..
git clone GitLab GitClone
ls
cd GitClone
```

### 21. Clone Remote Repository
```bash
git clone https://github.com/username/repository.git
```

### 22. Add Remote Repository
```bash
git remote add origin https://github.com/username/repository.git
git remote -v
```

### 23. Push to GitHub
```bash
git push -u origin main
git push
```

### 24. Pull Latest Changes
```bash
git pull origin main
```

### 25. Fetch Changes
```bash
git fetch
```

### 26. View Differences
```bash
git diff
```

### 27. Remove File from Git
```bash
git rm file2.txt
git commit -m "Removed file2"
```

### 28. Rename File
```bash
mv file1.txt newfile.txt
git status
git add .
git commit -m "Renamed file"
```

### 29. Show Repository Information
```bash
git branch
git status
git log
git remote -v
git config --list
```

---

### Complete Practical Questions – Git

**Question 1**
```bash
mkdir Practical
cd Practical
git init
touch demo.txt
cat > demo.txt
# type data, Ctrl+D
git status
git add .
git commit -m "Initial Commit"
git log --oneline
```

**Question 2**
```bash
git branch feature
git checkout feature
echo "Feature Data" >> demo.txt
git add .
git commit -m "Feature Commit"
git checkout master
git merge feature
git branch -d feature
git log --oneline
```

**Question 3**
```bash
cd ..
git clone Practical PracticalCopy
cd PracticalCopy
git status
```

**Question 4 (GitHub)**
```bash
git remote add origin https://github.com/username/repository.git
git remote -v
git push -u origin main
git pull origin main
```

---

## Docker Practical

### 1. Open Ubuntu & Terminal
Same as before.

### 2. Check Docker Installation
```bash
docker --version
sudo systemctl status docker
sudo systemctl start docker
sudo systemctl enable docker
docker --version
docker info
```

### 3. Basic Docker Commands
```bash
docker images
docker ps
docker ps -a
```

### 4. Download an Existing Image
```bash
docker pull ubuntu
docker images
```

### 5. Create and Run a Container
```bash
docker run -it --name mycontainer ubuntu
```
- `docker run` → create container
- `-it` → interactive terminal
- `--name mycontainer` → container name
- `ubuntu` → image name

Inside container:
```bash
pwd
ls
touch file1.txt
ls
exit
```

### 6. Start Existing Container
```bash
docker start mycontainer
```

### 7. Attach to Container
```bash
docker attach mycontainer
exit
```

### 8. Execute Command Without Attach
```bash
docker exec -it mycontainer bash
pwd
ls
exit
```

### 9. Copy File: Host → Container
```bash
echo "Hello Docker" > hostfile.txt
docker cp hostfile.txt mycontainer:/root/
docker exec -it mycontainer bash
cd /root
ls
cat hostfile.txt
exit
```

### 10. Copy File: Container → Host
```bash
docker cp mycontainer:/root/hostfile.txt .
ls
```

### 11. Commit Container as New Image
```bash
docker commit mycontainer myimage:v1
docker images
```

### 12. Run New Image
```bash
docker run -it myimage:v1
exit
```

### 13. Remove Container
```bash
docker stop mycontainer
docker rm mycontainer
```

### 14. Remove Image
```bash
docker rmi myimage:v1
```

### 15. Build a Fresh Docker Image
```bash
mkdir DockerDemo
cd DockerDemo
nano Dockerfile
```
Dockerfile content:
```dockerfile
FROM ubuntu
RUN apt-get update
CMD ["bash"]
```
Save: `Ctrl+O`, `Enter`, `Ctrl+X`
```bash
docker build -t ubuntu-demo .
docker images
docker run -it ubuntu-demo
exit
```

### 16. Build Apache/Nginx Web Server Image
```bash
mkdir WebDemo
cd WebDemo
nano index.html
```
```html
<html>
<body>
<h1>Welcome to CDAC Docker Practical</h1>
</body>
</html>
```
```bash
nano Dockerfile
```
```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```
```bash
docker build -t mywebsite .
```

### 17. Run Website Container
```bash
docker run -d -p 8080:80 --name webcontainer mywebsite
docker ps
```

### 18. Access Website in Browser
Open browser → `http://localhost:8080` → should show:
`Welcome to CDAC Docker Practical`

### 19–21. Stop / Restart / Remove
```bash
docker stop webcontainer
docker start webcontainer
docker rm -f webcontainer
```

### 22–24. Logs, Inspect, History
```bash
docker logs webcontainer
docker inspect webcontainer
docker history mywebsite
```

---

### Complete Practical Questions – Docker

**Question 1**
```bash
docker pull ubuntu
docker images
docker run -it --name demo ubuntu
touch test.txt
ls
exit
docker ps -a
```

**Question 2**
```bash
docker start demo
docker exec -it demo bash
echo "CDAC Docker" > file.txt
exit
docker cp demo:/file.txt .
ls
```

**Question 3**
```bash
mkdir Demo
cd Demo
nano Dockerfile
```
```dockerfile
FROM ubuntu
RUN apt-get update
CMD ["bash"]
```
```bash
docker build -t demoimage .
docker images
docker run -it demoimage
```

**Question 4 (Website)**
```bash
mkdir Website
cd Website
nano index.html
```
```html
<html>
<body>
<h1>Hello Docker</h1>
</body>
</html>
```
```bash
nano Dockerfile
```
```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html/index.html
```
```bash
docker build -t website .
docker run -d -p 8080:80 website
```
Open browser → `http://localhost:8080`

---


---

## Shell Scripting Practical

### 1. Create and Run a Script

```bash
nano myscript.sh
```
Every script starts with a **shebang** line:
```bash
#!/bin/bash
echo "Hello CDAC"
```
Save (`Ctrl+O`, `Enter`, `Ctrl+X`), then give execute permission and run:
```bash
chmod +x myscript.sh
./myscript.sh
# or
bash myscript.sh
```

---

### 2. Variables

```bash
#!/bin/bash
name="CDAC"
course=PGDAC
echo "Welcome to $name"
echo "Course: ${course}"
```
> No spaces around `=`. Access value with `$variable` or `${variable}`.

---

### 3. Command Line Arguments

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
echo "Number of arguments: $#"
```
Run with:
```bash
./myscript.sh Linux Docker
```

---

### 4. Read User Input

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello $name, Welcome!"

# Read multiple values
read -p "Enter two numbers: " a b
echo "Sum = $((a + b))"
```

---

### 5. Arithmetic Operations

```bash
#!/bin/bash
a=10
b=3
echo "Add: $((a + b))"
echo "Sub: $((a - b))"
echo "Mul: $((a * b))"
echo "Div: $((a / b))"
echo "Mod: $((a % b))"

# Alternative using expr
sum=$(expr $a + $b)
echo "Sum using expr: $sum"

# Alternative using let
let result=a+b
echo "Result using let: $result"
```

---

### 6. Conditional Statements

**if / else**
```bash
#!/bin/bash
read -p "Enter a number: " n
if [ $n -gt 0 ]
then
    echo "Positive Number"
else
    echo "Negative Number"
fi
```

**if / elif / else**
```bash
#!/bin/bash
read -p "Enter a number: " n
if [ $n -gt 0 ]
then
    echo "Positive"
elif [ $n -lt 0 ]
then
    echo "Negative"
else
    echo "Zero"
fi
```

**Common test operators**
```
-eq   equal to
-ne   not equal to
-gt   greater than
-lt   less than
-ge   greater than or equal to
-le   less than or equal to
-z    string is empty
-n    string is not empty
==    string equal (inside [[ ]])
&&    AND
||    OR
```

---

### 7. Loops

**for loop**
```bash
#!/bin/bash
for i in 1 2 3 4 5
do
    echo "Number: $i"
done

# for loop using range
for i in {1..5}
do
    echo "Value: $i"
done

# C-style for loop
for ((i=1; i<=5; i++))
do
    echo "i = $i"
done
```

**while loop**
```bash
#!/bin/bash
i=1
while [ $i -le 5 ]
do
    echo "i = $i"
    i=$((i + 1))
done
```

**until loop**
```bash
#!/bin/bash
i=1
until [ $i -gt 5 ]
do
    echo "i = $i"
    i=$((i + 1))
done
```

---

### 8. Case Statement

```bash
#!/bin/bash
read -p "Enter a choice (1-3): " choice
case $choice in
    1) echo "You selected Linux" ;;
    2) echo "You selected Git" ;;
    3) echo "You selected Docker" ;;
    *) echo "Invalid choice" ;;
esac
```

---

### 9. Functions

```bash
#!/bin/bash
greet() {
    echo "Hello $1, welcome to CDAC"
}

add() {
    result=$(($1 + $2))
    echo "Sum = $result"
}

greet "Student"
add 5 10
```

---

### 10. Arrays

```bash
#!/bin/bash
fruits=("Apple" "Banana" "Mango")
echo "First: ${fruits[0]}"
echo "All: ${fruits[@]}"
echo "Count: ${#fruits[@]}"

for fruit in "${fruits[@]}"
do
    echo "Fruit: $fruit"
done
```

---

### 11. String Operations

```bash
#!/bin/bash
str="Hello CDAC"
echo "Length: ${#str}"
echo "Substring: ${str:0:5}"
echo "Uppercase: ${str^^}"
echo "Lowercase: ${str,,}"
```

---

## Common Exam Programs (Ready to Use)

### 1. Factorial of a Number
```bash
#!/bin/bash
read -p "Enter a number: " n
fact=1
for ((i=1; i<=n; i++))
do
    fact=$((fact * i))
done
echo "Factorial of $n = $fact"
```

### 2. Fibonacci Series
```bash
#!/bin/bash
read -p "Enter number of terms: " n
a=0
b=1
echo "Fibonacci Series:"
for ((i=1; i<=n; i++))
do
    echo -n "$a "
    fn=$((a + b))
    a=$b
    b=$fn
done
echo
```

### 3. Check Prime Number
```bash
#!/bin/bash
read -p "Enter a number: " n
flag=0
if [ $n -le 1 ]
then
    flag=1
fi
for ((i=2; i<=n/2; i++))
do
    if [ $((n % i)) -eq 0 ]
    then
        flag=1
        break
    fi
done
if [ $flag -eq 0 ]
then
    echo "$n is Prime"
else
    echo "$n is Not Prime"
fi
```

### 4. Palindrome Check (Number)
```bash
#!/bin/bash
read -p "Enter a number: " n
orig=$n
rev=0
while [ $n -gt 0 ]
do
    digit=$((n % 10))
    rev=$((rev * 10 + digit))
    n=$((n / 10))
done
if [ $rev -eq $orig ]
then
    echo "Palindrome"
else
    echo "Not Palindrome"
fi
```

### 5. Reverse a Number
```bash
#!/bin/bash
read -p "Enter a number: " n
rev=0
while [ $n -gt 0 ]
do
    digit=$((n % 10))
    rev=$((rev * 10 + digit))
    n=$((n / 10))
done
echo "Reversed Number: $rev"
```

### 6. Sum of Digits
```bash
#!/bin/bash
read -p "Enter a number: " n
sum=0
while [ $n -gt 0 ]
do
    digit=$((n % 10))
    sum=$((sum + digit))
    n=$((n / 10))
done
echo "Sum of digits: $sum"
```

### 7. Armstrong Number Check
```bash
#!/bin/bash
read -p "Enter a number: " n
orig=$n
sum=0
while [ $n -gt 0 ]
do
    digit=$((n % 10))
    sum=$((sum + digit * digit * digit))
    n=$((n / 10))
done
if [ $sum -eq $orig ]
then
    echo "Armstrong Number"
else
    echo "Not an Armstrong Number"
fi
```

### 8. Swap Two Numbers
```bash
#!/bin/bash
read -p "Enter first number: " a
read -p "Enter second number: " b
temp=$a
a=$b
b=$temp
echo "After swap: a=$a, b=$b"
```

### 9. Biggest of Three Numbers
```bash
#!/bin/bash
read -p "Enter three numbers: " a b c
if [ $a -ge $b ] && [ $a -ge $c ]
then
    echo "$a is the biggest"
elif [ $b -ge $a ] && [ $b -ge $c ]
then
    echo "$b is the biggest"
else
    echo "$c is the biggest"
fi
```

### 10. Multiplication Table
```bash
#!/bin/bash
read -p "Enter a number: " n
for ((i=1; i<=10; i++))
do
    echo "$n x $i = $((n * i))"
done
```

### 11. Even or Odd
```bash
#!/bin/bash
read -p "Enter a number: " n
if [ $((n % 2)) -eq 0 ]
then
    echo "Even Number"
else
    echo "Odd Number"
fi
```

### 12. Sum of Natural Numbers (1 to N)
```bash
#!/bin/bash
read -p "Enter N: " n
sum=0
for ((i=1; i<=n; i++))
do
    sum=$((sum + i))
done
echo "Sum = $sum"
```

### 13. Reverse a String
```bash
#!/bin/bash
read -p "Enter a string: " str
rev=$(echo "$str" | rev)
echo "Reversed String: $rev"
```

### 14. Check String Palindrome
```bash
#!/bin/bash
read -p "Enter a string: " str
rev=$(echo "$str" | rev)
if [ "$str" == "$rev" ]
then
    echo "Palindrome String"
else
    echo "Not a Palindrome String"
fi
```

### 15. Count Vowels in a String
```bash
#!/bin/bash
read -p "Enter a string: " str
count=0
for (( i=0; i<${#str}; i++ ))
do
    ch=${str:$i:1}
    case $ch in
        [aeiouAEIOU]) count=$((count + 1)) ;;
    esac
done
echo "Number of vowels: $count"
```

---

## Most Important Shell Scripting Commands / Concepts
```
#!/bin/bash
chmod +x script.sh
./script.sh
read, read -p
echo, echo -n
$0 $1 $2 $@ $#
$(( ))          arithmetic expansion
expr, let
if / elif / else / fi
[ condition ]   or  [[ condition ]]
for, while, until
case ... esac
function definition: name() { ... }
arrays: arr=(a b c), ${arr[@]}, ${#arr[@]}
string: ${#str}, ${str:0:n}, ${str^^}, ${str,,}
```

---

## Quick Reference

### Linux
```
pwd, ls, ls -l, ls -a, cd, mkdir, mkdir -p, touch, cat, cp, mv, rm,
rmdir, find, grep, wc, head, tail, sort, chmod, whoami, id,
useradd, passwd, su, userdel, hostname, date, cal, free -h, df -h,
ps, kill, tar, zip, unzip
```

### Git
```
git --version
git config --global user.name
git config --global user.email
git config --list
git init
git status
git add .
git commit -m "message"
git log
git log --oneline
git branch
git checkout
git switch
git merge
git clone
git remote add origin
git remote -v
git push
git pull
git fetch
git diff
git rm
```

### Docker
```
docker --version, docker info, docker images, docker ps, docker ps -a,
docker pull, docker run, docker exec, docker attach, docker start,
docker stop, docker restart, docker rm, docker rmi, docker cp,
docker commit, docker build, docker logs, docker inspect, docker history,
docker image ls, docker container ls
```

---

## Notes for Exam Day
- ✅ All commands above run correctly on the Ubuntu exam VM.
- ✅ Git commands can be practiced beforehand in **Git Bash** on Windows.
- ⚠️ Docker, `sudo useradd/passwd/userdel`, and `systemctl` commands **cannot** be practiced in Git Bash — need the VM or Docker Desktop.
- ⚠️ Check `git branch` before using `checkout master` vs `checkout main` — depends on the VM's default branch name.
- ⚠️ Run `git config --list` first in the exam to check if name/email are already set before configuring again.
