**This project is not active. If you need to make changes, please fork it.**

# pivotaltracker-clubhouse
Simple tool to transfer stories from Pivotal Tracker to Clubhouse.

## Python Package Dependencies
I'm assuming you'll use pip to install them.
* requests 2.7.0 or above

## Usage
```
usage: pivotaltracker-clubhouse [-h] --ptoken PTOKEN --ctoken CTOKEN
                                --pproject PPROJECT --cproject CPROJECT

optional arguments:
  -h, --help           show this help message and exit

required arguments:
  --ptoken PTOKEN      The app token of the Pivotal Tracker user. See
                       https://www.pivotaltracker.com/help/articles/api_token/
  --ctoken CTOKEN      An app token of the Clubhouse user. See
                       https://clubhouse.io/api/v1/#authentication
  --pproject PPROJECT  The Pivotal Tracker project ID from which to transfer
                       stories.
  --cproject CPROJECT  The Clubhouse project ID to which to transfer stories.
```

## API Token Retrieval Instructions
* https://www.pivotaltracker.com/help/articles/api_token/
* https://clubhouse.io/api/rest/v2/#Authentication

## Notes

* Release-type stories are not transferred.
* Some basic information, such as the name, story type, tasks, and labels are preserved. Not all information is preserved. See the code for details.
* The created date will be the date of the transfer, and the requester will be the owner of the Clubhouse API token.
* The completion date will be set to the date the Pivotal story was "accepted".
* The work state (e.g. started, finished) is not preserved.
* If you run the tool multiple times, **you will have duplicate stories.**
   * You can easily bulk archive stories in Clubhouse before using the tool again, but if you want them permanently deleted, it won't be so easy (but archiving is probably sufficient to keep it uncluttered).
* An additional label "pivotal" is attached to each imported story.
* The Clubhouse story `external_id` is set to the ID of the Pivotal story.
* Stories in Pivotal are preserved, not deleted.
