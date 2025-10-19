# Taste of Sweetness

## Description
This floor feels like a digital world. The space is an illusion, all pink and sweet, stretching around you in impossible patterns. Here, you are no longer a climber but just another user.

Ahead, a door glows faintly. It is the only path forward and requires a level of authority you do not yet have. Fragments of session memory flicker, hinting at what it might take to gain higher access.

## Solve
**Flag:** `citadel{fru1tc4k3_4nd_c00k13s}`

- In this challenge, since the site dashboard clearly stated that only ADMIN can get the secret message so, it was clear that we most probably needed to change the cookie values to get the flag.
- Therefore, using the inspect option, I looked up the cookies for the session. In that I changed the value to the cookie to ADMIN and reloaded the site to get the flag.