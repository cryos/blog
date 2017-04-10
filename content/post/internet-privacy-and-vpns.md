+++
categories = ["general"]
tags = ["security", "privacy"]
images = ["images/201704-cloud-eyes.jpg"]
banner = "images/201704-cloud-eyes.jpg"
date = "2017-04-09T11:11:00-05:00"
title = "Internet Privacy and VPNs"
menu = ""
description = "I am sure you are sick of reading about Internet privacy, but after spending longer than might be advisable I have added a VPN, some browser plugins, and made a few changes"

+++

I am sure you have seen one or two articles already about the [demise of Internet privacy protections at the ISP level][nyt_isp_privacy], coupled with a crippling lack of competition in the USA. Last I checked I have only one realistic option from our cable company, and one far less realistic option of extremely slow DSL (by modern standards). Trying to liken the ISPs right to collect and sell data as akin to that of the websites we choose to visit seems vacuous at best.

This whole thing got me thinking about taking Internet privacy more seriously, and I wanted to find a [reputable virtual private network (VPN) provider][lifehacker_vpn] to enable us to remove our ISPs ability to sell my family's Internet activity. I found so many fake review sites offering to recommend whatever they were affiliated with, but with some persistence came across some resources that seemed more authentic.

[That one privacy site][tops] looks very well researched, and is referenced from a number of other articles about choosing a good VPN provider. If anything that site can be a little overwhelming, but it is clearly well researched. There are also some good subreddits, and people writing articles much like this one summarizing their own conclusions. Part of it is  figuring out what is important to you, and how much you are willing to pay for it. You must realize that you are shifting your trust from your ISP to your VPN provider.

I have seen some articles that seem particularly ill-conceived, such as a recent [TechCrunch article on rolling your own VPN][techcrunch_vpn]. This is entirely possible, but the cloud providers make no promises about protecting your data, and the bandwidth charges are likely to accumulate quickly. One of the major reasons to consider paying for VPN is to remove the ability to record and sell _your_ browsing data. Reputable VPN companies have been around for a while, choose one whose primary business model is protecting your privacy. Things to look for:

 * No logs policy
 * Servers close to your location
 * Good bandwidth, peering
 * Good security practices, prevent DNS/IPv6 leaks
 * Offer OpenVPN, other well established and secure protocols
 * High strength encryption offered
 * Requires minimal personal information from you
 
I ended up choosing [Mullvad][mullvad], for now at least, I liked the look of [IVPN][ivpn] and a few others too. They all seem to think people only need 3-5 connections, I guess I am an outlier here but you can use your router. I flashed the [AsusWRT-Merlin][asus_merlin] firmware onto my router, and set up OpenVPN. It was easy enough to get that set up, along with my Linux machines and Android devices. I failed on the Chromebook so far.

I added/ensured a number of browser extensions were installed, including [HTTPS Everywhere][https_everywhere], [uBlock Origin][ublock], and [Diconnect][disconnect]. For the places where I have complete control I am using HTTPS, and for the others where I have influence I am doing what I can to impress upon those in control that this is an important issue for a number of reasons. Still trying to make sure I maintain the right balance, and will continue to read around.

Some may ask why someone who uses social media, and freely shares many aspects of their life, using their real name, might feel inclined to take these precautions. For me it has always been about choice, I choose where, when, and what I share. I am also able to change my mind, delete accounts, etc. I find it extremely creepy when Facebook shows me adverts for things I just looked at on another site, I do not consent to them tracking me across sites.

The Internet is about freedom, and unfortunately the country I was born in and the one I currently call home are eroding those freedoms. The people making these decisions seem to lack the necessary understanding to realize that inserting backdoors, denying the right to strong encryption, and logging so many aspects of our lives is a serious erosion of our rights.

I expect my encrypted phone to be secure, and I shouldn't be forced to reveal login credentials to law enforcement or immigration officials without valid warrants and a lawyer present. I have always tried to follow the rule that anything I place online could be made public, I wouldn't worry too much, but I still expect my right to privacy to be protected.

I think we have learned in recent years that you have every right to be paranoid...there are often eyes lurking in the dark corners watching you ;-)

[nyt_isp_privacy]: https://www.nytimes.com/2017/04/03/technology/trump-repeal-online-privacy-protections.html
[lifehacker_vpn]: https://lifehacker.com/why-is-everyone-talking-about-vpns-1793768312
[tops]: https://thatoneprivacysite.net/
[techcrunch_vpn]: https://techcrunch.com/2017/04/09/how-i-made-my-own-vpn-server-in-15-minutes/
[mullvad]: https://mullvad.net/
[ivpn]: https://www.ivpn.net/
[asus_merlin]: https://asuswrt.lostrealm.ca/
[https_everywhere]: https://www.eff.org/HTTPS-EVERYWHERE
[ublock]: https://github.com/gorhill/uBlock
[disconnect]: https://disconnect.me/
