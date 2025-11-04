EXP-4: Perform Various GIT and DOCKER Operations


---

🧩 9. Perform Various GIT Operations (Local + Remote)

Basic Git Setup (First Time Only)

git config --global user.name "YourName"
git config --global user.email "youremail@example.com"

Create Local Repository

mkdir myproject
cd myproject
git init
echo "Hello Git" > readme.txt
git add readme.txt
git commit -m "Initial commit"

Connect to Remote Repository (GitHub Example)

git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main


---

🐋 10. Pull Ubuntu Image in Docker and Execute Bash

sudo docker pull ubuntu
sudo docker images          # Verify image
sudo docker run -it ubuntu bash

✅ You’ll now be inside the Ubuntu container shell:
root@<container_id>:/#


---

📂 11. Pull Files from GitHub, Modify, and Push

Clone Repository

git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

Modify or Add Files

echo "Updated content" >> file.txt

Stage, Commit, and Push Changes

git add file.txt
git commit -m "Updated file.txt with new content"
git push origin main


---

🧱 12. Docker Image Management

List Images

sudo docker images

Pull an Image

sudo docker pull nginx

Remove an Image

sudo docker rmi nginx


---

⚙️ 13. Basic Docker Commands

sudo docker ps            # List running containers
sudo docker ps -a         # List all containers
sudo docker start <container_id>
sudo docker stop <container_id>
sudo docker rm <container_id>
sudo docker rmi <image_id>
sudo docker run hello-world   # Test container


---

📘 14. Basic Git Commands

git init                  # Initialize repo
git status                # Check file status
git add <file>            # Stage file
git commit -m "message"   # Commit changes
git log                   # View commit history
git branch                # List branches
git checkout -b dev       # Create new branch
git merge dev             # Merge branch
git push / git pull       # Sync with remote


---

🏗️ 15. Create Git Repo → Add File → Commit → Push

mkdir myrepo
cd myrepo
git init
echo "Hello from AWS" > hello.txt
git add hello.txt
git commit -m "Added hello.txt file"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main

✅ Check your GitHub — your file should appear there!


---

🧰 16. Install Docker and Git on Ubuntu

Step 1 — Update Packages

sudo apt update -y

Step 2 — Install Docker

sudo apt install docker.io -y

Step 3 — Start Docker Service

sudo systemctl start docker
sudo systemctl enable docker
docker --version
# Example output: Docker version 24.0.5, build ced0996

Step 4 — Install Git

sudo apt install git -y
git --version
# Example output: git version 2.34.1


---

🔗 Extra Commands Used

git remote set-url origin https://github.com/Newton0921/prav.git
git push -u origin main
sudo docker run -it ubuntu bash
