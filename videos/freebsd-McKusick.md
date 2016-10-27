* Video link : (Series on Safari) [https://www.safaribooksonline.com/library/view/introduction-to-the/9780134306049/part1.html]
* Speaker : Marshall Kirk McKusick

# Processes
* have text (actual code), data (text/initialized, bss/non-initialized), heap and stack
* states can be new/running/sleeping/stopped/zombie
* process can be in zombie state because still waiting for parent to collect its status
* It can also be zombie if it is still waiting to write to a socket, since tcp sockets need to guarantee reliability
* In first case, init process will immediately clean up process once its parent is gone
* In second case, process will hang around
