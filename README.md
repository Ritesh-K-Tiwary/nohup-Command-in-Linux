# nohup-Command-in-Linux
Basic introduction about nohup command in linux.

### **What is `nohup`?**  
`nohup` (short for **No Hang Up**) is a Linux command that allows you to run a command or script in the background, ensuring that it **continues running even after you log out or close the terminal**.

### **How Does `nohup` Help?**  
1. **Prevents Process Termination on Logout:**  
   - When you close your terminal or disconnect from SSH, processes started with `nohup` keep running.
   
2. **Redirects Output to a File (`nohup.out`):**  
   - By default, `nohup` redirects both **stdout (standard output)** and **stderr (error output)** to `nohup.out`, so you can check logs later.

3. **Useful for Long-Running Processes:**  
   - If you're running a process that takes a long time (e.g., backups, updates, or server scripts), `nohup` ensures it isn't interrupted.

### **Usage Examples**  
#### **1. Running a Command in the Background**
```bash
nohup python my_script.py &
```
- The `&` at the end runs the process in the background.
- The output is stored in `nohup.out` by default.

#### **2. Redirecting Output to a Custom Log File**
```bash
nohup ./long_running_script.sh > mylog.log 2>&1 &
```
- `> mylog.log`: Saves standard output to `mylog.log`.
- `2>&1`: Redirects error output (`stderr`) to the same log file.

#### **3. Checking Running Processes**
```bash
ps aux | grep my_script.py
```
- This helps you find the process ID (PID) of your background job.

#### **4. Killing a `nohup` Process**
```bash
kill -9 <PID>
```
- Replace `<PID>` with the actual process ID found using `ps aux`.

### **Alternatives to `nohup`**
- **`screen` or `tmux`**: Allows you to detach and reattach sessions.
- **`systemd` service**: More robust for managing persistent services.
- **`disown`**: Used in combination with `&` to remove a job from the shell’s job table.

