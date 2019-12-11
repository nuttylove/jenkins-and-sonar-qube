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

- [Setup Jenkins CI in 30 Minutes](https://mydeveloperplanet.com/2019/01/30/setup-jenkins-ci-in-30-minutes/)

# 2. Jenkins & Git

- ให้ทำการ <b>Generate SSH key</b> โดยเป็น User ของ Jenkins วิธีก็คือให้เปิด Terminal ขึ้นมาแล้วทำการพิมพ์คำสั่งนี้ลงไป `sudo su jenkins` เพื่อเข้าสู่ User Jenkins แล้วตามด้วยคำสั่ง `ssh-keygen` เพื่อทำการสร้าง SSH key

	- `sudo su jenkins-lts`

	- `Password:xxxxxxxxx`

	- `ssh-keygen`


# 3. SonarQube Installation

- Create or config file `sonar-project.properties` in project

- Install sonarqube and start server ผ่าน <b>Docker</b>

		docker run -d --name sonarqube -p 9000:9000 -p 9092:9092 sonarqube

- Install sonar-scanner ผ่าน <b>brew</b>

	- Install service

			brew install sonar-scanner

	- cd to project path

	- Scan project and update to server sonarqube

			sonar-scanner -X

			sonar-scanner -v

			sonar-scanner

- ถ้าใช้ NodeJS

	- cd to your project

	- Install package

			npm i sonar-scanner --save-dev

	- Setting script run in package.json

			"scripts": {
				...
				"sonar-scanner": "sonar-scanner"
			}

	- Scan project and update to server sonarqube

			npm run sonar-scanner

- Go to `server sonarqube` URL [http://localhost:9000](http://localhost:9000)

	- Username: <b>admin</b>

	- Password: <b>admin</b>


# 4. Setting up Continuous Integration With GitLab, Jenkins and SonarQube

- [Angular Fitbit = Jenkins + SonarQube](https://medium.com/polyglots-blog/angular-fitbit-jenkins-sonarqube-829cc6201469)

- [Continuous Integration Setup with GitLab, Jenkins and SonarQube](https://linuxhandbook.com/ci-with-gitlab-jenkins-and-sonarqube/)

- [ตรวจสอบคุณภาพของ Code ด้วย SonarQube](https://medium.com/@ifew/%E0%B8%95%E0%B8%A3%E0%B8%A7%E0%B8%88%E0%B8%AA%E0%B8%AD%E0%B8%9A%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%A0%E0%B8%B2%E0%B8%9E%E0%B8%82%E0%B8%AD%E0%B8%87-code-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-sonarqube-808fae32785a)