## 1. The systems which allow only one process execution at a time, are called __________  
a) uniprogramming systems  
b) uniprocessing systems  
c) unitasking systems  
d) none of the mentioned  
**View Answer**

**Answer:** b  
**Explanation:** Those systems which allow more than one process execution at a time, are called multiprocessing systems. Uniprocessing means only one processor.

## 2. In operating system, each process has its own __________  
a) address space and global variables  
b) open files  
c) pending alarms, signals and signal handlers  
d) all of the mentioned  
**View Answer**

**Answer:** d  
**Explanation:** In Operating Systems, each process has its own address space which contains code, data, stack and heap segments or sections. Each process also has a list of files which is opened by the process as well as all pending alarms, signals and various signal handlers.

## 3. In Unix, Which system call creates the new process?  
a) fork  
b) create  
c) new  
d) none of the mentioned  
**View Answer**

**Answer:** a  
**Explanation:** In UNIX, a new process is created by fork() system call. fork() system call returns a process ID which is generally the process id of the child process created.

**advertisement**

## 4. A process can be terminated due to __________  
a) normal exit  
b) fatal error  
c) killed by another process  
d) all of the mentioned  
**View Answer**

**Answer:** d  
**Explanation:** A process can be terminated normally by completing its task or because of fatal error or killed by another process or forcefully killed by a user. When the process completes its task without any error then it exits normally. The process may exit abnormally because of the occurrence of fatal error while it is running. The process can be killed or terminated forcefully by another process.

## 5. What is the ready state of a process?  
a) when process is scheduled to run after some execution  
b) when process is unable to run until some task has been completed  
c) when process is using the CPU  
d) none of the mentioned  
**View Answer**

**Answer:** a  
**Explanation:** Ready state of the process means process has all necessary resources which are required for execution of that process when CPU is allocated. Process is ready for execution but waiting for the CPU to be allocated.

**Note:** Join free Sanfoundry classes at [Telegram](https://t.me/sanfoundryclasses/) or [Youtube](https://www.youtube.com/c/SanfoundryOfficial/?sub_confirmation=1)

## 6. What is interprocess communication?  
a) communication within the process  
b) communication between two process  
c) communication between two threads of same process  
d) none of the mentioned  
**View Answer**

**Answer:** b  
**Explanation:** Interprocess Communication (IPC) is a communication mechanism that allows processes to communicate with each other and synchronise their actions without using the same address space. IPC can be achieved using shared memory and message passing.

## 7. A set of processes is deadlock if __________  
a) each process is blocked and will remain so forever  
b) each process is terminated  
c) all processes are trying to kill each other  
d) none of the mentioned  
**View Answer**

**Answer:** a  
**Explanation:** Deadlock is a situation which occurs because process A is waiting for one resource and holds another resource (blocking resource). At the same time another process B demands blocking a resource as it is already held by a process A, process B is waiting state unless and until process A releases occupied resource.

## 8. A process stack does not contain __________  
a) Function parameters  
b) Local variables  
c) Return addresses  
d) PID of child process  
**View Answer**

**Answer:** d  
**Explanation:** Process stack contains Function parameters, Local variables and Return address. It does not contain the PID of child process.

## 9. Which system call can be used by a parent process to determine the termination of child process?  
a) wait  
b) exit  
c) fork  
d) get  
**View Answer**

**Answer:** a  
**Explanation:** wait() system call is used by the parent process to determine termination of child process. The parent process uses wait() system call and gets the exit status of the child process as well as the pid of the child process which is terminated.

## 10. The address of the next instruction to be executed by the current process is provided by the __________  
a) CPU registers  
b) Program counter  
c) Process stack  
d) Pipe  
**View Answer**

**Answer:** b  
**Explanation:** The address of the next instruction to be executed by the current process is provided by the Program Counter. After every instruction is executed, the Program Counter is incremented by 1 i.e. address of the next instruction to be executed. CPU fetches instruction from the address denoted by Program Counter and execute it.


Which algorithm uses time quantum? A. Shortest job scheduling algorithm B. Round robin scheduling algorithm C. Priority scheduling algorithm D. Multilevel queue scheduling algorithm


>[!gemini]+ Gemini
>## Which algorithm uses time quantum?
> 
> - [ ] Shortest job scheduling algorithm
> - [ ] Round robin scheduling algorithm **(Correct)**
> - [ ] Priority scheduling algorithm
> - [ ] Multilevel queue scheduling algorithm
