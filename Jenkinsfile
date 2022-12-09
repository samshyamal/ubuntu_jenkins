#!groovy
import groovy.json.JsonSlurperClassic
node {

  def BUILD_NUMBER=env.BUILD_NUMBER
    def RUN_ARTIFACT_DIR="tests/${BUILD_NUMBER}"
    def SFDC_USERNAME

    def HUB_ORG=avinesh17@force.com
    def SFDC_HOST = https://login.salesforce.com
    def JWT_KEY_CRED_ID = env.JWT_CRED_ID_DH
    def CONNECTED_APP_CONSUMER_KEY=3MVG9n_HvETGhr3B6A3.exf_YzkwuSLGDVU6haN6jZZEe.SkgEhgCf6rhYXPxP6tqoWWkzuGbi8lvzY1PoVK7
    println 'KEY IS' 
    println JWT_KEY_CRED_ID
    println HUB_ORG
    println SFDC_HOST
    println CONNECTED_APP_CONSUMER_KEY

    def toolbelt = tool 'toolbelt'

    stage('Checkout Source') {
        // when running in multi-branch job, one must issue this command
        checkout scm
    }
	
 
	
    	      stage('authorisatiom') {
            if (isUnix()) {
                rc = sh returnStatus: true, script: "${toolbelt} force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername --instanceurl ${SFDC_HOST}"
            }else{
                 rc = bat returnStatus: true, script: "\"${toolbelt}\" force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile \"${JWT_KEY_CRED_ID}\" --setdefaultdevhubusername --instanceurl ${SFDC_HOST}"
            }
            if (rc != 0) { error 'hub org authorization failed' }
              }
        


}
