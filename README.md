# git_file_locker

dirty hack to lock file in git repo, to work on that file in atomic manner.

once one user has locked a file, others will not be able to push changes on that, untill unlocked by him.
lock is valid for upto cetrain hours, that can be configured.

# how to use

put content of `client/cmd` in client's machine executable path.

put content of `server/cmd` in server's machine executable path.

put content of `server/hooks` in server's machine git repo's hooks folder.

make cmds + hooks executable

and you are good to go.


# acquiring/releasing/querying lock
      $./client/cmd/git-lock [--ack|--rel|--query] [file_to_lock]
      --ack                        Try to acquire lock.
      --rel                        Try to release lock.
      --query                      Check if file is already locked.
      --ack | --rel | --query      flags are mutually exclusive.
      -h|--help                    Print this help and exit.

# todo
Files existance and their strictness from repo's root is not implemented

This script check for syncronised file read/write, however it is not meant for aggressive operations, no testing is done for that. As i assume in real world there are too few requests in a narrow band of time to git repo, so this will work most of the time.

# warnings and know attack
This is not a fully developed app, its just a hack to work on project files, so this is not meant for file control on bigger level.

User of file is either fetched from config or from commiter, however those can be manipulated by using command directly.




