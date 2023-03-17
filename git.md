When pushing to remote repo that's private using auth tokens:
1. Set remote origin including the token:
```bash
git remote add origin "https://[token]@github.com/[username]/[repository].git"
```
3. Push to branch
```
git push -u origin main
```