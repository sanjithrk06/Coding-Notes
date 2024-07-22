- All the file in the stagging area will be tracked under git.
- The files in our working directory will be untracked.

> **To track the file**
- `git add .` to add all the untracked files in the folder to stagging area.
- If you want to add the specific file, then `git add FILE_NAME` to add the specific file.
- You can also unstage the added file.

> **Commit**
- To commit the file(i.e. moving the files from stagging area to repo), 
	`git commit -m "COMMIT DESCRIPTION"`
- Always you need to give the commit message in the git command after `-m`.
- If you give commit with message, you will be opening a new file to add commit message or it may open in the terminal itself (as vim). 
- If it is file, you need to write message and save the file and close it. If it is Vim then you need to write the message and to close press `ESC -> : -> q`.

> **Log the changes**
- To print the log, use the command
	`git log`
	It will print recent commits with the description and author.
- If you need to print the logs in oneline, then
	`git log --oneline`
	It will print the recent commit Id with description.

> **Atomic Commits**
- It is nothing but a procedure to when you need to commit.
	- Keep commits centric to one feature, one component or one fix. Focused on one thing.

