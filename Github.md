
### To set remote to push to 2 repos at the same time

- Create a new remote in the name `all`,
	`git remote add all https://github.com/sanjithrk06/Backend.git`,
- Add the push url,
	`git remote set-url --add --push all https://github.com/sanjithrk06/Ezlil-API.git`
- Add the another push url,
	`git remote set-url --add --push all https://github.com/sanjithrk06/Backend.git`,
- Check it, `git remote -v`.