# Jenkins & SonarQube Installation

Jenkins, SonarQube and Git Install and Setup

# 1. Jenkins Installation

- <b>`Download`</b> the official Jenkins image from Docker Hub with this docker command:

  		docker pull jenkins/jenkins

- <b>`start`</b> a new Jenkins container from the downloaded image with the following command:
  
   		docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts

- หรือ <b>`brew install`</b>

		brew install jenkins-lts

- <b>`access`</b> [http://localhost:8080](http://localhost:8080) to show the initial Jenkins unlock screen:

- paste the <b>`pre-generated`</b> admin password which will be in the file location specified as well as on the console output during the previous docker run command

- หน้านี้เจ้าตัว Jenkins จะถามหา Password เพื่อทำการ unlock วิธีการเอา Password มาให้ทำการเปิด Terminal ขึ้นมาแล้วใช้คำสั่งนี้
<b>`sudo cat ตามด้วย path ที่เป็นตัวหนังสือสีแดง`</b>

		sudo cat /Users/bugaboo/.jenkins/secrets/initialAdminPassword

- Start Jenkins

		brew services start jenkins-lts

- Restart Jenkins

		brew services restart jenkins-lts

- Go to URL [http://localhost:8080/](http://localhost:8080/)

# 2. Jenkins & Git

- ให้ทำการ <b>Generate SSH key</b> โดยเป็น User ของ Jenkins วิธีก็คือให้เปิด Terminal ขึ้นมาแล้วทำการพิมพ์คำสั่งนี้ลงไป `sudo su jenkins` เพื่อเข้าสู่ User Jenkins แล้วตามด้วยคำสั่ง `ssh-keygen` เพื่อทำการสร้าง SSH key

	- `sudo su jenkins-lts`

	- `Password:xxxxxxxxx`

	- `ssh-keygen`


# 3. SonarQube Installation

- ถ้ายังไม่มี SonarQube ให้ใช้ Docker ในการติดตั้ง

		docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube

	*** [Angular Fitbit = Jenkins + SonarQube](https://medium.com/polyglots-blog/angular-fitbit-jenkins-sonarqube-829cc6201469)