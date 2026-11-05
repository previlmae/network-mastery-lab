# Week 1: Lab setup + OSI/TCP-IP refresh

**Goal:** A working lab, a live repo, and OSI/ports recall from memory.

## Sessions

| Day | Session | Outcome | Done |
| --- | --- | --- | --- |
| D1 | Set up lab + repo, OSI from memory | Repo live; OSI one-pager committed | ☐ |
| D2 | Top 25 ports + Anki deck | Deck built; 22/25 correct on second pass | ☐ |
| D3 | Capture a TCP handshake in Wireshark | Annotated handshake screenshot | ☐ |
| D4 | Cabling refresh + build office-v0 in Packet Tracer | office-v0.pkt + diagram; 100% ping success | ☐ |
| D5 | Weekly review | Quiz ≥ 80%; weekly log entry | ☐ |

## Evidence

D3: TCP three-way handshake (Wireshark)

TCP three-way handshake between my Mac and Notion

What I captured: my Mac opening a secure (HTTPS) connection to Notion, isolated with the display filter tcp.stream eq 7.

Handshake time: 7.182441 − 7.024786 = 0.158 s (158 ms) from SYN to SYN-ACK.
Ports: 443 is HTTPS on Notion's side; 61199 is a temporary port my Mac picked for this one conversation.
Confirmed it was Notion: the TLS Client Hello right after the handshake (packet 389) shows SNI=www.notion.com.
Bonus: troubleshooting a slow app

Notion felt slow, so I used the same capture to check whether my network was the cause.

Found Notion's connections with tls.handshake.extensions_server_name contains "notion" (12 connections).
Timed the handshake: Notion answered in 0.158 s.
Checked for lost data with tcp.analysis.retransmission && tcp.stream eq 7: 32 resent packets out of 12,850 (0.25%), in two short bursts.

Conclusion: my network checked out fine, so the slowness was on Notion's side, either their servers or the app itself. I timed one of the 12 connections; the rest of the traffic looked healthy.

<!-- Link screenshots, .pkt files, captures and notes saved in this folder -->

## Weekly log

- **What clicked:**
- **What didn't:**
- **Quiz score:**
- **Focus for next week:**
