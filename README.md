Thinkpad Fan Control Daemon
--------------------
Simple fan controller. No configuration required since temperature limits are taken from the coretemp sensors. 

### Operation

Once the maximum temperature is passed the fan will be switched to 'full-speed', otherwise the fan will be left on 'auto'. Uses a linear regression to (hopefully) allow for smooth fan speed transitions.

Great success on an overheating T420 (i7)

### Installation

Prepare Modules
  
    $ modprobe thinkpad_acpi fan_control=1
    $ modprobe coretemp
    
Build
  
    $ git clone git://github.com/dolch/tp_fancontrol.git
    $ cd tp_fancontrol
    $ ./autogen.sh
    $ ./configure
    $ make
    $ make install
   
Complete

    $ systemctl start tp_fancontrol
    
