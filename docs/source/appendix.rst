.. _appendix:

Appendix
========

Original bash code for taskloop:

.. code-block:: bash

    #!/bin/bash
    #Path to task binary
    TASK=/usr/local/bin/task
    #Flag to break out of the while loop
    CONTINUE=1
    COUNT=0
    TAGS='+work'

    #were we given a project name?  Nope?  Ask for one
    if [ -z $1 ];then
        echo -n "Which project? "
        read PROJECT
    else
        PROJECT=$1
    fi
        
    #Ignore $1, for tags
    shift
    for tag in "$@"
    do
        if [ $tag == "" ];then
            echo "not adding nothing"
        else
            TAGS="$TAGS +$tag"
        fi
    done
    #Loop through the tasks, adding to the project
    echo "Adding to project: $PROJECT"
    echo "Using tags: $TAGS"

    while [ $CONTINUE -eq 1 ]; do
        echo -n 'Task Description (<CR> to end): '
        read TASKDESC
        if [[ $TASKDESC == '' ]]; then
            echo "$(basename $0) processed $COUNT tasks"
            if [[ $COUNT -gt 0 ]];then
                echo "Syncing to remote" && ${TASK} sync
            fi
            exit 0
        else
            ${TASK} add rc.hooks=0 project:$PROJECT $TAGS "$TASKDESC"
            COUNT=$((COUNT+1))
        fi
    done
