### check previous doc [Simple IVR](https://github.com/hrshuv0/Asterisk/blob/main/simple%20asterisk%20call.md)

# call and choose options

## configure sip.conf

#### add with previous users

    [6598]
    type=friend
    host=dynamic
    secret=6598
    context=internal

## configure sip.conf

    exten => s,1,Answer(500)
     same => n, dial(SIP/6598, 2)
     ;same => n(loop),Background(please-try-again,50)
     same => n(loop),Playback(please-try-again)
     same => n,WaitExten()
 
    exten => 1,1,Playback(you-entered)
     same => n,SayNumber(1)
     same => n, Playback(tt-monkeys)
     same => n,Goto(s,loop)
 
    exten => 2,1,Playback(you-entered)
     same => n,SayNumber(2)
     same => n, Playback(tt-weasels)
     same => n,Goto(s,loop)
 
    exten => 3,1,Playback(you-entered)
     same => n,SayNumber(3)
     same => n, Playback(tt-monkeysintro)
     same => n,Goto(s,loop)
 
    exten => 6598,1,Goto(internal,s,1)
   
   
