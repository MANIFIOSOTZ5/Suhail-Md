## Deploy on VPS or PC.
- You need to Install git,ffmpeg,curl,nodejs,yarn with pm2 
   1. Install git ffmpeg curl 
      ``` 
       sudo apt -y update &&  sudo apt -y upgrade 
       sudo apt -y install git ffmpeg curl
      ``` 
   2. Install nodejs  
      ```   
      sudo apt -y remove nodejs
      curl -fsSl https://deb.nodesource.com/setup_lts.x | sudo bash - && sudo apt -y install nodejs
      ```
  
   3. Install yarn
      ```
      curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - 
      echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
      sudo apt -y update && sudo apt -y install yarn
      ```  
  
   4. Install pm2
      ```
      sudo yarn global add pm2
      ```
  
   5. Clone Repo and install required packages
      ```
      git clone https://github.com/SuhailTechInfo/Suhail-Md
      cd Suhail-Md
      yarn install --network-concurrency 1
      ```

   6. Create an env file for ENV. 
      ```
      touch config.env
      nano config.env
      ```
      copy paste lines below.

      ```
      OWNER_NUMBER="255622452339"
      SESSION_ID = "SUHAIL_23_44_04_02_ewogICJjcmVkcy5qc29uIjogIntcIm5vaXNlS2V5XCI6e1wicHJpdmF0ZVwiOntcInR5cGVcIjpcIkJ1ZmZlclwiLFwiZGF0YVwiOlwiRU1YeHU4Mll4TUtxZ2NrS0ZIL0c0Q3NCMDhteG1rR3BQVityc0tOMlhYcz1cIn0sXCJwdWJsaWNcIjp7XCJ0eXBlXCI6XCJCdWZmZXJcIixcImRhdGFcIjpcIjh5eWpRL09RaXd1MUZLTXFLM2RXMzZtV2NHcmU4amRNMHluSGxTZVdVVms9XCJ9fSxcInBhaXJpbmdFcGhlbWVyYWxLZXlQYWlyXCI6e1wicHJpdmF0ZVwiOntcInR5cGVcIjpcIkJ1ZmZlclwiLFwiZGF0YVwiOlwiaUtaT2pxTmhsWXlxWVRyaWRubnZwd0NrWEEyemd3VzVDYVdBVG16MTIyZz1cIn0sXCJwdWJsaWNcIjp7XCJ0eXBlXCI6XCJCdWZmZXJcIixcImRhdGFcIjpcIjYzYnUxRjU0T2ZKV1VCSk1GZlkzRjJjemVGY1NnQVBFQU9qaGtkN0VzRU09XCJ9fSxcInNpZ25lZElkZW50aXR5S2V5XCI6e1wicHJpdmF0ZVwiOntcInR5cGVcIjpcIkJ1ZmZlclwiLFwiZGF0YVwiOlwidU1GTzVQYXhOV1NCZzdEV0RlTktFSnVzYzhsL1VObUwyMFFjYWFLYWwxST1cIn0sXCJwdWJsaWNcIjp7XCJ0eXBlXCI6XCJCdWZmZXJcIixcImRhdGFcIjpcIitrc1k0Z2RvSUh6N0w5Y1BuNERENGRMNG9IM3RzNG1abDJPUDZBeFhUV1k9XCJ9fSxcInNpZ25lZFByZUtleVwiOntcImtleVBhaXJcIjp7XCJwcml2YXRlXCI6e1widHlwZVwiOlwiQnVmZmVyXCIsXCJkYXRhXCI6XCJRUFJRMHRzNVJVQmNwY2x2SG8yTHQvbUN1ZUJhMWo2bWhjMlhuODBFZG1nPVwifSxcInB1YmxpY1wiOntcInR5cGVcIjpcIkJ1ZmZlclwiLFwiZGF0YVwiOlwiSzA1L2xJcjNDZ01iNGFpQmlPajFKSGJpQnZ5LzVzckl1ZTFZRnVCVmQwdz1cIn19LFwic2lnbmF0dXJlXCI6e1widHlwZVwiOlwiQnVmZmVyXCIsXCJkYXRhXCI6XCJvaElZd2tjcWN2ZHdlUXpCNEoyS25HSXJRV080YzBBc01SSVhzU2lYT3hjTENqRDduMmIyc0ZOSERkaHBKczhwWnorY1o2R0c2NzNsQlVLbVVjd2NqQT09XCJ9LFwia2V5SWRcIjoxfSxcInJlZ2lzdHJhdGlvbklkXCI6MTE5LFwiYWR2U2VjcmV0S2V5XCI6XCIzaFBYQ0lTclFOai9TenlLZ2w1M3A1ZElWWmlDSEVpMC85bWZjbHNjcEJVPVwiLFwicHJvY2Vzc2VkSGlzdG9yeU1lc3NhZ2VzXCI6W3tcImtleVwiOntcInJlbW90ZUppZFwiOlwiMjU1NjIyNDUyMzM5QHMud2hhdHNhcHAubmV0XCIsXCJmcm9tTWVcIjp0cnVlLFwiaWRcIjpcIkI5OUU1RkM1RUUwRDA0N0M2OUI5MzgzRTgwMUZFQTM1XCJ9LFwibWVzc2FnZVRpbWVzdGFtcFwiOjE3MTIxMDE0ODR9XSxcIm5leHRQcmVLZXlJZFwiOjMxLFwiZmlyc3RVbnVwbG9hZGVkUHJlS2V5SWRcIjozMSxcImFjY291bnRTeW5jQ291bnRlclwiOjAsXCJhY2NvdW50U2V0dGluZ3NcIjp7XCJ1bmFyY2hpdmVDaGF0c1wiOmZhbHNlfSxcImRldmljZUlkXCI6XCJLenpHMUI1OFNEU0JmR1BiV05wM2tBXCIsXCJwaG9uZUlkXCI6XCJmNjk0N2M4NS05OGUxLTQ1MWYtOGZhOS0xOWUxM2ViZDhiNzhcIixcImlkZW50aXR5SWRcIjp7XCJ0eXBlXCI6XCJCdWZmZXJcIixcImRhdGFcIjpcInh4TWhtRFBvQ2NjRnI2dzRnL3Z1R1pNMFFkMD1cIn0sXCJyZWdpc3RlcmVkXCI6dHJ1ZSxcImJhY2t1cFRva2VuXCI6e1widHlwZVwiOlwiQnVmZmVyXCIsXCJkYXRhXCI6XCJrM09Kd3dKMHg4YngxV0M3TWZ4bXNvYU1QZ3M9XCJ9LFwicmVnaXN0cmF0aW9uXCI6e30sXCJwYWlyaW5nQ29kZVwiOlwiV1pSUTFYU0hcIixcIm1lXCI6e1wiaWRcIjpcIjI1NTYyMjQ1MjMzOTozMUBzLndoYXRzYXBwLm5ldFwiLFwibGlkXCI6XCI3NTk5OTcxNDc3MTE0ODozMUBsaWRcIixcIm5hbWVcIjpcIvCfmYHimLnvuI/wn5it8J+ZgfCfmK3wn5mB4pi577iP8J+ZgVwifSxcImFjY291bnRcIjp7XCJkZXRhaWxzXCI6XCJDTDcwb0lvQ0VPR3dzckFHR0FJZ0FDZ0FcIixcImFjY291bnRTaWduYXR1cmVLZXlcIjpcIjZyMDk2YzA4bk1HNk9ueCtKM2pUNkhyeEIrMWZVTDlVck1hZDVhR0VxazA9XCIsXCJhY2NvdW50U2lnbmF0dXJlXCI6XCJ1c2piU1R1bWkrRHRKYTBUb2R1aFI0YWozV1daTVNqcFJzS0RYV3ZCa1NjTDJsWGtkY1loSnVhRVUxcWd1WXJ4bzdGTzI5MEpOdlBVVGlDb0lRK3BCZz09XCIsXCJkZXZpY2VTaWduYXR1cmVcIjpcIm8wV2FWNkI0MWtxVEVBcmx3RjEza2MxVHI2ZWlNY3ZOdTg0bVBMSUpVdVJEbDRvSFptUE1HZDFvd2N1N2NtQU1XaEdIaXA2cGx1Zlhta0V6ZWszTWdBPT1cIn0sXCJzaWduYWxJZGVudGl0aWVzXCI6W3tcImlkZW50aWZpZXJcIjp7XCJuYW1lXCI6XCIyNTU2MjI0NTIzMzk6MzFAcy53aGF0c2FwcC5uZXRcIixcImRldmljZUlkXCI6MH0sXCJpZGVudGlmaWVyS2V5XCI6e1widHlwZVwiOlwiQnVmZmVyXCIsXCJkYXRhXCI6XCJCZXE5UGVuTlBKekJ1anA4ZmlkNDAraDY4UWZ0WDFDL1ZLekduZVdoaEtwTlwifX1dLFwicGxhdGZvcm1cIjpcImFuZHJvaWRcIixcImxhc3RBY2NvdW50U3luY1RpbWVzdGFtcFwiOjE3MTIxMDE0NzgsXCJteUFwcFN0YXRlS2V5SWRcIjpcIkFBQUFBQXBSXCJ9IiwKICAiYXBwLXN0YXRlLXN5bmMta2V5LUFBQUFBQXBSLmpzb24iOiAie1wia2V5RGF0YVwiOlwickxraUpKSEJEbnQ0SlpUMVVBRTlyVlBLblAxZVZqQnIvUGNKcXhtRXJLbz1cIixcImZpbmdlcnByaW50XCI6e1wicmF3SWRcIjo1NTgzODE2MzAsXCJjdXJyZW50SW5kZXhcIjoxLFwiZGV2aWNlSW5kZXhlc1wiOlswLDFdfSxcInRpbWVzdGFtcFwiOlwiMTcxMTgwOTIzODk3N1wifSIKfQ=="
      THUMB_IMAGE = "https://telegra.ph/file/d5b1c3544fedc23e11a06.jpg"
      OWNER_NAME = "▒☠️●▬๑۩𝘔𝘈𝘕𝘐𝘍𝘐𝘖𝘚𝘖𝘛𝘡 ۩๑▬●☠️▒"
      PREFIX = .
      WARN_COUNT = 3
      DISABLE_PM = "false"
      THEME= "SUHAIL"
      MODE = "public"
      ANTILINK_VALUES = "https://,chat.whatsapp.com"
      
      ```
      ctrl + o and ctrl + x, To save and exit

   7. start and stop bot
 
      To start bot ``` npm start ```,
      To stop bot ``` npm stop ```

 
<h2 align="center">  NOTICE </h2>
---
- *Suhail-Md is not made by `WhatsApp Inc.` Sometimes or misusing the bot might `ban` your `WhatsApp account!`*
- *In that case, I'm not responsible for banning your account.*
- *Use Suhail-Md at your own risk by keeping this warning in mind.*
 
