#!groovy

@Library('github.com/red-panda-ci/jenkins-pipeline-library@v3.1.5') _

// Initialize global config
cfg = jplConfig('general-concepts', 'doc', '', [slack: '#integrations', email:'redpandaci+general-concepts@gmail.com'])

pipeline {
    agent none

    stages {
        stage ('Initialize') {
            agent { label 'master' }
            steps  {
                jplStart(cfg)
            }
        }
        stage ('Make release'){
            agent { label 'master' }
            when { branch 'release/new' }
            steps {
                script { cfg.promoteBuild.enabled = true }
                jplMakeRelease(cfg)
            }
        }
    }

    post {
        always {
            jplPostBuild(cfg)
        }
    }

    options {
        timestamps()
        ansiColor('xterm')
        buildDiscarder(logRotator(artifactNumToKeepStr: '20',artifactDaysToKeepStr: '30'))
        disableConcurrentBuilds()
        skipDefaultCheckout()
        timeout(time: 1, unit: 'DAYS')
    }
}
