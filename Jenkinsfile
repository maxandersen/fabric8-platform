#!/usr/bin/groovy
node{
  ws{
    checkout scm
    sh "git remote set-url origin git@github.com:fabric8io/fabric8-platform.git"

    def pipeline = load 'release.groovy'

    stage 'Stage'
    def stagedProject = pipeline.stage()

    stage 'Approve'
    pipeline.approve(stagedProject)

    stage 'Promote'
    pipeline.release(stagedProject)
  }
}
