#!/bin/bash

COMMIT_FILE="$1"

set -e

# OSX GUI apps do not pick up environment variables the same way as Terminal apps and there are no easy solutions,
# especially as Apple changes the GUI app behavior every release (see https://stackoverflow.com/q/135688/483528). As a
# workaround to allow GitHub Desktop to work, add this (hopefully harmless) setting here.

export PATH=$PATH:/usr/local/bin

FORBIDDEN="[iv]\d{6}"


exit_status=0
if grep -c -q -E "$FORBIDDEN" -i "$COMMIT_FILE"; then
    COMMIT_MSG=$(cat $COMMIT_FILE)
    echo "Commit message contains vKey - commit aborted!"
    echo ">>>"
    echo "$COMMIT_MSG"
    echo ">>>"
    exit_status=1
fi

exit $exit_status
