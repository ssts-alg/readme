## Here is how to run Jenkins as root - this will cause the maven plugin processes to also run as root.

#### Method 1) 
Modify the following line in JENKINS_USER in /etc/sysconfig/jenkins
  #JENKINS_USER=jenkins
  JENKINS_USER=root
In Debian-based systems, the file is located at /etc/default/jenkins

### Method 2) 
Directly modify /etc/init.d/jenkins
  #daemon --user "$JENKINS_USER" --pidfile "$JENKINS_PID_FILE" $JAVA_CMD $PARAMS > /dev/null
  echo "WARNING: RUNNING AS ROOT"
  daemon --user root --pidfile "$JENKINS_PID_FILE" $JAVA_CMD $PARAMS > /dev/null
Then, of course, you must run:

#### Restart Jenkins
```service jenkins restart```
