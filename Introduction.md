# nhm01
nhm01 is the University of Oslo Natural History Museum's High Processing Computer. 

# Applying for an account on nhm01
If you need an account at nhm01, and you work at the museum, then email me at j.f.fleming(@)nhm.uio.no. This email should include the short form of your UiO username. I’ll forward it on to the Drift team, and normally this gets sorted in about a week.

# Getting Started
Logging into nhm01 can be a little more challenging than some other similar HPCs, as it requires a "Proxy Jump". Proxy Jumps are a way to use another server (in this case the University's login server) as a middle-way between two points.
To log in to nhm01, use the following command, replacing \<user\> with your username:

ssh -J \<user\>@login.uio.no \<user\>@nhm01.uio.no 

If you need to copy files to nhm01, you can do it like this:

scp -o 'ProxyJump \<user\>@login.uio.no' \<filename\> \<user\>@nhm01.uio.no:/destination/of/copy

