# Jenkins & SonarQube Installation

Jenkins, SonarQube and Git Install and Setup

# 1. Jenkins Installation

- `Download` the official Jenkins image from Docker Hub with this docker command:

  		docker pull jenkins/jenkins

- `start` a new Jenkins container from the downloaded image with the following command:
  
   		docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts

- หรือ `brew install`

		brew install jenkins

- `access` [http://localhost:8080](http://localhost:8080) to show the initial Jenkins unlock screen:

- paste the `pre-generated` admin password which will be in the file location specified as well as on the console output during the previous docker run command

- หน้านี้เจ้าตัว Jenkins จะถามหา Password เพื่อทำการ unlock วิธีการเอา Password มาให้ทำการเปิด Terminal ขึ้นมาแล้วใช้คำสั่งนี้
`sudo cat ตามด้วย path ที่เป็นตัวหนังสือสีแดง`

		sudo cat /Users/bugaboo/.jenkins/secrets/master.key

# 2. SonarQube Installation

- ถ้ายังไม่มี SonarQube ให้ใช้ Docker ในการติดตั้ง

		docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube