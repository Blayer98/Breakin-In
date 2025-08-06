A Server Emulator for The Sims Bustin Out (PS2)'s Online Weekend mode, written in C# targeting .NET Core.
This fork is by Blayer98.

## What is The Sims Bustin' Out Free Weekend?
The Free Weekend mode in Bustin' Out was the second arm of The Sims' short foray into online multiplayer. Unlike in The Sims Online, which is an MMO where you control one sim at a time, Bustin' Out lets the host control the entire family present at their house, while the invited player controls a visitor. 

The purpose of this mode was to let players help each other through the campaign mode (via trading money or unlocks), or show off their modifications to the different properties in the game.

Join a lobby with someone else in it. You can chat in the lobby with the R1 button. If you invite someone to your game, they will come to the property you've saved on in single player mode.

Both players can pause the game at any time, though both players must hold R1 to enter high speed mode. You cannot enter Build/Buy, and job carpools are disabled, so make sure you've got everything you want on your lot before you mess around in multiplayer.

## Server Usage
Clone the repo into a folder and configure it using config.json. The only important thing to set here is your _external ip_, which is used by the redirection server the game first connects to.

Run the server using:
`dotnet run`
That's it for getting the server itself working. To get the game to connect to it, you need to trick the DNS into redirecting some EA and Sony URLs to your server.

A good way to do this is to host a DNS server. On Linux, the easiest way to do this is to install `dnsmasq`, then add the following to your hosts file:
```
199.195.251.151 gate1.us.dnas.playstation.org
<your public ip> tso-e.com
<your public ip> ps2sims04.ea.com
```
The top is a DNAS replacement server hosted by someone else.

Make sure ports `11100`, `10901` and `53` (dns) are open on your firewall.

## Future Stuff
The Report function does not work. (ReptIn and ReptOut need to be added)

More error code handling and additions.

Password verification does not work and the user can enter any password, the server will accept the login anyway.

Sometimes leaving a chatroom does not work correctly and the game will softlock.

Find Sim does not work properly.
(onln needs the following data: A and R/ROOM)

a string called "***BROADCAST***" is in the game files but unsure is this was ever used during the official server's lifecycle.

Europe/Korean/Japan copies needs their ports to be added to connect to the server.

Trading unlocks seems to not work properly?

## Acknowledgements 

- Me for noticing that Need for Speed Underground used the same connection packet as Bustin' Out sent.
- The creator of the NFSU Server, which was the basis of this server (although it was a bit incredibly unsafe for a server). (https://github.com/HarpyWar/nfsuserver/)
- Whoever recorded those packets for a (literally) underground PC/PS2 racing game in 2003, arguably before anyone even cared about this kind of preservation
- PCSX2 developers and the PS2 online community for making DNAS less of an insurmountable obstacle.
- ripperiperi for creating the original Breakin In server!
