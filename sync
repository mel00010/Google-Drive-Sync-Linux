#!/bin/bash

function usage ()
{
       echo "Usage:"
       echo "        sync [--version|--repeat|--help|--once]"
}

function version ()
{
       echo "Google Drive Sync Version 1.0.6"
}
function sync ()
{
        pull
        push
}

function pull ()
{
        cd $DRIVEPATH
        echo "Pulling from drive..."
        drive pull -ignore-conflict=true -r=true -ignore-name-clashes=true -no-clobber=false -no-prompt=true -force=false
}

function push ()
{
        cd $DRIVEPATH
        echo "Pushing to drive..."
        drive push -ignore-conflict=true -r=true -convert=false -ignore-name-clashes=true -no-prompt=true -no-clobber=false -force=false
}

case $1 in
        --version|-v)
                version
                exit 0
        ;;
        --help|-h)
                usage
                exit 0
        ;;
        --repeat|-r)
                while true
                do
                        echo "Syncing Google Drive on repeat."
                        echo "Press [CTRL+C] three times to stop.."
                        sync
                        sleep 60
                done 
                exit 0
        ;;
        --once|-o)
                echo "Syncing Google Drive once."
                echo "Press [CTRL+C] twice to stop.."
                sync
                exit 0
        ;;
        -*)
                echo "Error: no such option $1"
                usage
                exit 1
        ;;
esac
usage
