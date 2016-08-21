#!/usr/bin/env groovy

def deployment(target) 
{
    echo 'Deploy $target'

    if (target == 'develop')
    {
        //unstash 'develop_archive'
        echo 'deloy develop version'
    }
    else
    {
        echo 'deply release version'
    }
}

node 
{
  stage 'Checkout'
  echo 'pull source code'
  
  stage 'Build'
  parallel (
      'develop': {
          echo "Build develop version"
          //stash includes: 'output/develop/*', name: 'develop_archive'
          //deployment('develop')
      },
      'staging': {
          echo "Build staging version"
          //deployment('release')
      },
      'production': {
          echo "Build production version"
          //deployment('release')
      }
  )
  
  stage 'Deploy'
  deployment('release')
}
