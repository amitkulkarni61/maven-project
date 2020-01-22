pipeline {

agent any

stages
{

stage('cloning code')

{

steps

{git 'https://github.com/amitkulkarni61/maven-project.git'
}
}

stage('compile my project')
{
steps
{
withMaven(jdk: 'JAVA home', maven: 'Maven home') {
    sh 'mvn compile'
}}}
    
stage('test my project')
{
steps
{
withMaven(jdk: 'JAVA home', maven: 'Maven home') {
    sh 'mvn test'
}}}
    
stage('package my project')
{
steps
{
withMaven(jdk: 'JAVA home', maven: 'Maven home') {
    sh 'mvn package'
}}}
    

    
        
stage('package my install')
{
steps
{
withMaven(jdk: 'JAVA home', maven: 'Maven home') {
    sh 'mvn install'
}}}
	
   
	
	
stage('deploy to  tomcat')
{
steps
{
    sshagent(['tomcat']) {
	 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.27.184:/var/lib/tomcat/webapps'
						}
}
}
    
    
    

}
}
