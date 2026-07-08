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

### Common Viva Questions – Docker

**What is Docker?**
A containerization platform used to package and run applications with all their dependencies.

**Difference between Image and Container?**
- Image: Read-only template.
- Container: Running instance of an image.

**Difference between Dockerfile and Image?**
- Dockerfile: Instructions to build an image.
- Image: Output created after building the Dockerfile.

**What does `docker build` do?**
Builds an image from a Dockerfile.

**What does `docker run` do?**
Creates and starts a new container.

**What does `docker exec` do?**
Runs a command inside an already running container.

**What does `docker cp` do?**
Copies files between the host system and a container.

**What does `-p 8080:80` mean?**
Maps host port 8080 to container port 80, allowing the web application to be accessed through the browser.

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


- ✅ All commands above run correctly on the Ubuntu exam VM.
- ✅ Git commands can be practiced beforehand in **Git Bash** on Windows.
- ⚠️ Docker, `sudo useradd/passwd/userdel`, and `systemctl` commands **cannot** be practiced in Git Bash — need the VM or Docker Desktop.
- ⚠️ Check `git branch` before using `checkout master` vs `checkout main` — depends on the VM's default branch name.
- ⚠️ Run `git config --list` first in the exam to check if name/email are already set before configuring again.
