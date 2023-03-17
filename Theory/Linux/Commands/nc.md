# File transfer
On receiving end:
```bash
nc -l -p 1234 > out.file
```
On sending end:
```bash
nc -w 3 [destination] 1234 < out.file
```