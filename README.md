# HAOS Automation Examples

This repository provides YAML examples for Home Assistant (HAOS) automations, offering practical solutions and use cases for various smart home scenarios.

## Morning Automation Example

I created this automation because I was tired of making custom ringtones for my iPhone just to use as my morning alarm. I have fond memories of the 90s, when I’d set my radio alarm clock to my favorite station to wake up for school. So, why not make use of my Spotify playlist? While Amazon Alexa offers routines, most of my smart home setup was already managed through Home Assistant, so I wanted a solution that would work seamlessly with HAOS and my bedside lamps.

I also realized it would be much more convenient to have the weather forecast reported automatically, rather than having to ask Alexa for it every morning. Combining these ideas, I built this automation to deliver a hands-free morning routine. I later added a PIR motion sensor that sends motion detection data via an ESP8266 chip. HAOS can then trigger a shutoff for my lights and music on my Echo Dot after I've left the bedroom. 
 
---

The `spotify_alarm_morning_routine.yaml` file demonstrates a comprehensive morning routine that integrates smart lighting, weather updates, and music playback:

- The routine begins by gradually increasing the brightness of a pair of Cync A19 light bulbs (integrated using the Matter protocol) over 5 minutes.
- After the lights start brightening, the Alexa Media Player integration uses text-to-speech (TTS) to announce the weather forecast. Weather data is sourced from Accuweather entities, and filters are applied to ensure the day’s high and low temperatures are spoken as whole numbers.
- When the bulbs reach 75% brightness, a Spotify morning playlist starts playing on a designated Amazon Echo device. The automation is configured to shuffle the playlist, so you don’t hear the same first song every day.
- The lights continue brightening to 100% over the next 5 minutes.
- After 45 minutes, the lights and music automatically turn off.

For further energy efficiency, you can use a motion sensor to detect inactivity and set up a separate automation. If no motion is detected for a set period, the automation will turn off all devices involved in the routine (such as the lights and music playback).

---

**Requirements for Spotify playback:**

- The `SpotifyPlus` integration from HACS is required to control Spotify playback.
- The `Alexa Media Player` integration is also installed via HACS.
- You will need a Spotify Premium account to enable playback on preferred devices.
- Have your Spotify playlist URI ready; the playlist ID is a 22-character string.
- A delay was added to the Actions for Spotify to give it enough time to transfer playback to your preferred device.

---
