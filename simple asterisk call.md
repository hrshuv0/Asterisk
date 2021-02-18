# Simple IVR

## Need to congigure 3 different file in /etc/asterisk directory.

1. sip.conf
2. extensions.conf
3. voicemail.conf

#### before configure you should have to backup those files.
## you can copy those files to backup in another file as original

    sudo cp sip.conf sip.conf.orig
    sudo cp extensions.conf extensions.conf.orig
    sudo cp voicemail.conf voicemail.conf.orig
    
    
## configure sip.conf
#### you can remove all data in this file and add some required line or add line in at top

    [general]
    context=internal
    allowguest=no
    #bindport=5060
    bindaddr=0.0.0.0
    srvlookup=no
    disallow=all
    allow=ulaw
    alwaysauthreject=yes
    canreinvite=no
    nat=yes
    session-time=refuse
    localnet=192.168.1.13/255.255.255.0
    
    [7001]
    type=friend
    host=dynamic
    secret=123
    context=internal
    
    [7002]
    type=friend
    host=dynamic
    secret=456
    context=internal
    
    
## configure extensions.conf

    [internal]
    exten => 7001,1,Answer()
    exten => 7001,2,Dial(SIP/7001,60)
    exten => 7001,3,Playback(vm-nobodyavail)
    exten => 7001,4,VoiceMail(7001@main)
    exten => 7001,5,hangup()

    exten => 7001,1,Answer()
    exten => 7001,2,Dial(SIP/7001,60)
    exten => 7001,3,Playback(vm-nobodyavail)
    exten => 7001,4,VoiceMail(7001@main)
    exten => 7001,5,hangup()

    exten => 8001,1,VoicemailMain(7001@main)
    exten => 8001,2,Hangup()

    exten => 8002,1,VoicemailMain(7001@main)
    exten => 8002,2,Hangup()

## configure voicemail.conf

    [main]
    7001 => 123
    7002 => 456


