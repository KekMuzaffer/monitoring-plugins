#!/bin/bash

# get the current timestamp in the format YYYYMMDDHHMMSS
current_time="$(date +"%Y%m%d%H%M%S")"

# directory where tripwire stores its report files
TRIPWIRE_REPORT_PATH="/var/lib/tripwire/report/"

# get the name of the most recent tripwire report file
TRIPWIRE_LAST_FILE_NAME="$(ls -ltr ${TRIPWIRE_REPORT_PATH} | tail -n 1 | awk '{print $NF}')"

# extract the timestamp from the latest tripwire report filename
# assumes filename contains a timestamp like: <n>-YYYYMMDD-HHMMSS.*
# steps:
# - isolate filename
# - cut relevant date/time parts
# - remove separators to match YYYYMMDDHHMMSS format
TRIPWIRE_LAST_FILE_TIMESTAMP="$(ls -ltr ${TRIPWIRE_REPORT_PATH} | tail -n 1 | awk '{print $NF}' | cut -d'-' -f2,3 | cut -d'.' -f1 | sed 's/-//g')"

# threshold (in "timestamp difference" units) beyond which reports are considered outdated
# note: this is a simple numeric comparison, not true time arithmetic
CRITICAL_TIME=10500

EXIT_CODE_OK=0
EXIT_CODE_CRITICAL=2

# calculate the difference between current time and last report timestamp
# this works because both values are in YYYYMMDDHHMMSS numeric format
((verify_file_age=current_time-TRIPWIRE_LAST_FILE_TIMESTAMP))

# check if the report is too old
if [[ ${verify_file_age} -gt ${CRITICAL_TIME} ]]; then
    printf "Tripwire reports are no longer generated.\n"
    exit ${EXIT_CODE_CRITICAL}
else
    printf "Tripwire reports are up to date: Last tripwire file ${TRIPWIRE_LAST_FILE_NAME}.\n"
    exit ${EXIT_CODE_OK}
fi
