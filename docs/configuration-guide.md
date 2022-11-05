
<span id='account'></span>**[account](#user-content-account)** <samp>`{type: object}`</samp>
  - <span id='account-username'></span>**[username](#user-content-account-username)** <samp>`{type: string}`</samp> : The in-game playername of the account
  - <span id='account-password'></span>**[password](#user-content-account-password)** <samp>`{type: string}`</samp> : The password of the account (only required for Mojang accounts, leave it empty for Microsoft accounts. Microsoft accounts will just get instructions in the console to put a token into [microsoft.com/link](https://microsoft.com/link)
  - <span id='account-auth'></span>**[auth](#user-content-account-auth)** <samp>`{type: string}`</samp> <samp>`{default: "microsoft"}`</samp> : Authentication type (options: 'microsoft', 'mojang', 'offline')

<span id='discord'></span>**[discord](#user-content-discord)** <samp>`{type: object}`</samp>
  - <span id='discord-active'></span>**[active](#user-content-discord-active)** <samp>`{type: boolean}`</samp> : Whether to send Discord webhooks
  - <span id='discord-webhook'></span>**[webhook](#user-content-discord-webhook)** <samp>`{type: object}`</samp>
    - <span id='discord-webhook-spam'></span>**[spam](#user-content-discord-webhook-spam)** <samp>`{type: string}`</samp> : Url of webhook to relay position in queue, new tunnels, connects/disconnects, and other spam
    - <span id='discord-webhook-livechat'></span>**[livechat](#user-content-discord-webhook-livechat)** <samp>`{type: string}`</samp> : Url of webhook to relay livechat
    - <span id='discord-webhook-status'></span>**[status](#user-content-discord-webhook-status)** <samp>`{type: string}`</samp> : Url of webhook to relay pertinent info for connecting and nothing else (e.g. joining server, low queue position)
  - <span id='discord-color'></span>**[color](#user-content-discord-color)** <samp>`{type: number}`</samp> <samp>`{default: 2123412}`</samp> : Color of Discord embeds sent to the webhooks in **decimal value** (you can use convertingcolors.com to find the decimal value of a color you want)
  - <span id='discord-id'></span>**[id](#user-content-discord-id)** <samp>`{type: string}`</samp> : ID of the Discord user or role to ping when below the queueThreshold

<span id='queuethreshold'></span>**[queueThreshold](#user-content-queuethreshold)** <samp>`{type: number}`</samp> <samp>`{default: 21}`</samp> : Minimum queue position before toast notifications & Discord pings start getting sent

<span id='reconnectinterval'></span>**[reconnectInterval](#user-content-reconnectinterval)** <samp>`{type: number}`</samp> <samp>`{default: 69}`</samp> : Time (in seconds) between each reconnection attempt (see: [How to Auto-Reconnect with Supervisor](https://github.com/Enchoseon/2based2wait/wiki/How-to-Auto-Reconnect-with-Supervisor))

<span id='uncleandisconnectinterval'></span>**[uncleanDisconnectInterval](#user-content-uncleandisconnectinterval)** <samp>`{type: number}`</samp> <samp>`{default: 196}`</samp> : Time (in seconds) proxy will go without getting a single packet from 2B2T before assuming it was uncleanly disconnected and initiating a reconnect attempt

<span id='log'></span>**[log](#user-content-log)** <samp>`{type: object}`</samp>
  - <span id='log-active'></span>**[active](#user-content-log-active)** <samp>`{type: object}`</samp> : Settings for which logging categories should be enabled
    - <span id='log-active-error'></span>**[error](#user-content-log-active-error)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to log errors
    - <span id='log-active-proxy'></span>**[proxy](#user-content-log-active-proxy)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to log proxy status (e.g. connecting to server, starting Mineflayer, etc.)
    - <span id='log-active-chat'></span>**[chat](#user-content-log-active-chat)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to log chat
    - <span id='log-active-bridgeclientpackets'></span>**[bridgeClientPackets](#user-content-log-active-bridgeclientpackets)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to log packets being sent from the controller to the proxy
    - <span id='log-active-serverpackets'></span>**[serverPackets](#user-content-log-active-serverpackets)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to log packets being sent from 2b2t to the proxy
  - <span id='log-cutoff'></span>**[cutoff](#user-content-log-cutoff)** <samp>`{type: number}`</samp> <samp>`{default: 69000}`</samp> : Maximum size a log file can be (in bytes) before it gets split up
  - <span id='log-packetfilters'></span>**[packetFilters](#user-content-log-packetfilters)** <samp>`{type: object}`</samp> : Settings for which packets we shouldn't log
    - <span id='log-packetfilters-server'></span>**[server](#user-content-log-packetfilters-server)** <samp>`{type: array}`</samp> <samp>`{default: ["map","map_chunk","player_info","entity_metadata","entity_velocity","entity_move_look","entity_look","update_time","world_particles","unload_chunk","teams","rel_entity_move","entity_head_rotation","entity_update_attributes","block_change"]}`</samp> : Packets being sent from 2b2t to not log
    - <span id='log-packetfilters-bridgeclient'></span>**[bridgeClient](#user-content-log-packetfilters-bridgeclient)** <samp>`{type: array}`</samp> <samp>`{default: ["position","look","position_look","arm_animation"]}`</samp> : Packets being sent from the controller to not log
  - <span id='log-compression'></span>**[compression](#user-content-log-compression)** <samp>`{type: object}`</samp> : Settings for log compression. Tweak with caution. The default options maximize memory usage for the fastest speed
    - <span id='log-compression-active'></span>**[active](#user-content-log-compression-active)** <samp>`{type: boolean}`</samp> : **[Warning, Event Thread-Blocking!]** Whether to compress log files with Gzip. Leave this off unless you have a really good reason to enable it
    - <span id='log-compression-level'></span>**[level](#user-content-log-compression-level)** <samp>`{type: number}`</samp> <samp>`{default: 1}`</samp> : How much compression to apply between 1 and 9. Higher values result in better compression ratio at the expense of speed (**[Warning, Event Thread-Blocking!]**)
    - <span id='log-compression-memlevel'></span>**[memLevel](#user-content-log-compression-memlevel)** <samp>`{type: number}`</samp> <samp>`{default: 9}`</samp> : How much memory to allocate to the internal compression state between 1 and 9. Higher values result in better compression ratio and speed at the expense of memory usage
    - <span id='log-compression-windowbits'></span>**[windowBits](#user-content-log-compression-windowbits)** <samp>`{type: number}`</samp> <samp>`{default: 15}`</samp> : How much memory to allocate to the history buffer between 8 and 15. Higher values result in better compression ratio at the expense of memory usage
  - <span id='log-alwaysincrement'></span>**[alwaysIncrement](#user-content-log-alwaysincrement)** <samp>`{type: boolean}`</samp> : Whether to increment the log file every session (can lead to thousands of 1kb log files in production, but is pretty useful when rapidly testing during development)

<span id='server'></span>**[server](#user-content-server)** <samp>`{type: object}`</samp> : Settings for how the proxy connects to the server
  - <span id='server-host'></span>**[host](#user-content-server-host)** <samp>`{type: string}`</samp> <samp>`{default: "connect.2b2t.org"}`</samp> : Address of the server to connect to
  - <span id='server-version'></span>**[version](#user-content-server-version)** <samp>`{type: string}`</samp> <samp>`{default: "1.12.2"}`</samp> : Version of Minecraft the server is on 
  - <span id='server-port'></span>**[port](#user-content-server-port)** <samp>`{type: number}`</samp> <samp>`{default: 25565}`</samp> : Port of the server to connect to

<span id='proxy'></span>**[proxy](#user-content-proxy)** <samp>`{type: object}`</samp> : Settings for how you connect to the proxy
  - <span id='proxy-whitelist'></span>**[whitelist](#user-content-proxy-whitelist)** <samp>`{type: array}`</samp> : Playernames of accounts that are allowed to connect to the proxy
  - <span id='proxy-onlinemode'></span>**[onlineMode](#user-content-proxy-onlinemode)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to enable online-mode on the proxy. This probably should never be touched
  - <span id='proxy-port'></span>**[port](#user-content-proxy-port)** <samp>`{type: number}`</samp> <samp>`{default: 25565}`</samp> : Port on the machine to connect to the proxy

<span id='ngrok'></span>**[ngrok](#user-content-ngrok)** <samp>`{type: object}`</samp> : Settings for ngrok tunneling
  - <span id='ngrok-active'></span>**[active](#user-content-ngrok-active)** <samp>`{type: boolean}`</samp> : Whether to create an ngrok tunnel
  - <span id='ngrok-authtoken'></span>**[authtoken](#user-content-ngrok-authtoken)** <samp>`{type: string}`</samp> : The auth token for your Ngrok.io account
  - <span id='ngrok-region'></span>**[region](#user-content-ngrok-region)** <samp>`{type: string}`</samp> <samp>`{default: "us"}`</samp> : Tunnel region (options: 'us', 'eu', 'au', 'ap', 'sa', 'jp', or 'in')

<span id='mineflayer'></span>**[mineflayer](#user-content-mineflayer)** <samp>`{type: object}`</samp> : Settings for the mineflayer bot
  - <span id='mineflayer-active'></span>**[active](#user-content-mineflayer-active)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to enable Mineflayer
  - <span id='mineflayer-autoqueuemaininterval'></span>**[autoQueueMainInterval](#user-content-mineflayer-autoqueuemaininterval)** <samp>`{type: number}`</samp> <samp>`{default: 690}`</samp> : Time (in seconds) between every `/queue main` command
  - <span id='mineflayer-killaura'></span>**[killAura](#user-content-mineflayer-killaura)** <samp>`{type: object}`</samp> : Settings for killaura
    - <span id='mineflayer-killaura-interval'></span>**[interval](#user-content-mineflayer-killaura-interval)** <samp>`{type: number}`</samp> <samp>`{default: 0.69}`</samp> : Time (in seconds) between every attack attempt
    - <span id='mineflayer-killaura-blacklist'></span>**[blacklist](#user-content-mineflayer-killaura-blacklist)** <samp>`{type: array}`</samp> <samp>`{default: ["zombie_pigman","enderman"]}`</samp> : Array of mobs that will not be attacked
  - <span id='mineflayer-autoeat'></span>**[autoEat](#user-content-mineflayer-autoeat)** <samp>`{type: object}`</samp> : Settings for autoeat
    - <span id='mineflayer-autoeat-priority'></span>**[priority](#user-content-mineflayer-autoeat-priority)** <samp>`{type: string}`</samp> <samp>`{default: "saturation"}`</samp> : What type of food to prioritize eating (options: 'saturation', 'foodPoints', 'effectiveQuality')
    - <span id='mineflayer-autoeat-startat'></span>**[startAt](#user-content-mineflayer-autoeat-startat)** <samp>`{type: number}`</samp> <samp>`{default: 19}`</samp> : Hunger level at which to start eating
    - <span id='mineflayer-autoeat-bannedfood'></span>**[bannedFood](#user-content-mineflayer-autoeat-bannedfood)** <samp>`{type: array}`</samp> <samp>`{default: ["rotten_flesh","pufferfish","chorus_fruit","poisonous_potato","spider_eye"]}`</samp> : Foods that will not be eaten
  - <span id='mineflayer-antiafk'></span>**[antiAfk](#user-content-mineflayer-antiafk)** <samp>`{type: object}`</samp> : Settings for antiafk
    - <span id='mineflayer-antiafk-actions'></span>**[actions](#user-content-mineflayer-antiafk-actions)** <samp>`{type: array}`</samp> <samp>`{default: ["rotate"]}`</samp> : Actions the proxy can do (options: 'rotate', 'walk', 'jump', 'jumpWalk', 'swingArm', 'breakBlock')
    - <span id='mineflayer-antiafk-fishing'></span>**[fishing](#user-content-mineflayer-antiafk-fishing)** <samp>`{type: boolean}`</samp> : Whether the proxy will fish. The account must be standing in water and have a fishing rod to autofish.
    - <span id='mineflayer-antiafk-chatting'></span>**[chatting](#user-content-mineflayer-antiafk-chatting)** <samp>`{type: boolean}`</samp> : Whether the proxy will chat
    - <span id='mineflayer-antiafk-chatmessages'></span>**[chatMessages](#user-content-mineflayer-antiafk-chatmessages)** <samp>`{type: array}`</samp> <samp>`{default: ["!pt","!queue"]}`</samp> : Chat messages that the proxy will send if chatting is enabled
    - <span id='mineflayer-antiafk-chatinterval'></span>**[chatInterval](#user-content-mineflayer-antiafk-chatinterval)** <samp>`{type: number}`</samp> <samp>`{default: 690420}`</samp> : Time (in milliseconds) between each chat message

<span id='experimental'></span>**[experimental](#user-content-experimental)** <samp>`{type: object}`</samp> : Settings for experimental features that may be more unstable in resource usage and/or server and version parity
  - <span id='experimental-spoofplayerinfo'></span>**[spoofPlayerInfo](#user-content-experimental-spoofplayerinfo)** <samp>`{type: object}`</samp>
    - <span id='experimental-spoofplayerinfo-active'></span>**[active](#user-content-experimental-spoofplayerinfo-active)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to spoof the [Player Info packet](https://wiki.vg/Protocol#Player_Info) to set a custom skin
    - <span id='experimental-spoofplayerinfo-texture'></span>**[texture](#user-content-experimental-spoofplayerinfo-texture)** <samp>`{type: object}`</samp>
      - <span id='experimental-spoofplayerinfo-texture-value'></span>**[value](#user-content-experimental-spoofplayerinfo-texture-value)** <samp>`{type: string}`</samp> : Base64 string of skin from [https://sessionserver.mojang.com/session/minecraft/profile/<UUID>?unsigned=false](https://wiki.vg/Mojang_API#UUID_to_Profile_and_Skin.2FCape)
      - <span id='experimental-spoofplayerinfo-texture-signature'></span>**[signature](#user-content-experimental-spoofplayerinfo-texture-signature)** <samp>`{type: string}`</samp> : Base64 string of signed data using Yggdrasil's private key from [https://sessionserver.mojang.com/session/minecraft/profile/<UUID>?unsigned=false](https://wiki.vg/Mojang_API#UUID_to_Profile_and_Skin.2FCape)
  - <span id='experimental-spoofping'></span>**[spoofPing](#user-content-experimental-spoofping)** <samp>`{type: object}`</samp>
    - <span id='experimental-spoofping-active'></span>**[active](#user-content-experimental-spoofping-active)** <samp>`{type: boolean}`</samp> : Whether to spoof the [Status Response packet](https://wiki.vg/Server_List_Ping#Status_Response) when pinging the proxy server
    - <span id='experimental-spoofping-noresponse'></span>**[noResponse](#user-content-experimental-spoofping-noresponse)** <samp>`{type: boolean}`</samp> : Whether to cancel the response entirely. Otherwise, the packet described in fakeResponse will be sent.
    - <span id='experimental-spoofping-fakeresponse'></span>**[fakeResponse](#user-content-experimental-spoofping-fakeresponse)** <samp>`{type: object}`</samp>
      - <span id='experimental-spoofping-fakeresponse-version'></span>**[version](#user-content-experimental-spoofping-fakeresponse-version)** <samp>`{type: object}`</samp>
        - <span id='experimental-spoofping-fakeresponse-version-name'></span>**[name](#user-content-experimental-spoofping-fakeresponse-version-name)** <samp>`{type: string}`</samp> <samp>`{default: "1.12.2"}`</samp> : Spoofed server version
        - <span id='experimental-spoofping-fakeresponse-version-protocol'></span>**[protocol](#user-content-experimental-spoofping-fakeresponse-version-protocol)** <samp>`{type: number}`</samp> <samp>`{default: 340}`</samp> : Spoofed [protocol number](https://wiki.vg/Protocol_version_numbers)
      - <span id='experimental-spoofping-fakeresponse-players'></span>**[players](#user-content-experimental-spoofping-fakeresponse-players)** <samp>`{type: object}`</samp>
        - <span id='experimental-spoofping-fakeresponse-players-max'></span>**[max](#user-content-experimental-spoofping-fakeresponse-players-max)** <samp>`{type: number}`</samp> <samp>`{default: 20}`</samp> : Spoofed max players
        - <span id='experimental-spoofping-fakeresponse-players-online'></span>**[online](#user-content-experimental-spoofping-fakeresponse-players-online)** <samp>`{type: number}`</samp> : Spoofed number of players online
        - <span id='experimental-spoofping-fakeresponse-players-sample'></span>**[sample](#user-content-experimental-spoofping-fakeresponse-players-sample)** <samp>`{type: array}`</samp> <samp>`{default: []}`</samp>
            - <span id='experimental-spoofping-fakeresponse-players-sample-items-0-name'></span>**[name](#user-content-experimental-spoofping-fakeresponse-players-sample-items-0-name)** <samp>`{type: string}`</samp> : Spoofed playername
            - <span id='experimental-spoofping-fakeresponse-players-sample-items-0-id'></span>**[id](#user-content-experimental-spoofping-fakeresponse-players-sample-items-0-id)** <samp>`{type: string}`</samp> : Spoofed player UUID
      - <span id='experimental-spoofping-fakeresponse-description'></span>**[description](#user-content-experimental-spoofping-fakeresponse-description)** <samp>`{type: object}`</samp>
        - <span id='experimental-spoofping-fakeresponse-description-text'></span>**[text](#user-content-experimental-spoofping-fakeresponse-description-text)** <samp>`{type: string}`</samp> <samp>`{default: "A Minecraft server"}`</samp> : Spoofed MOTD
      - <span id='experimental-spoofping-fakeresponse-favicon'></span>**[favicon](#user-content-experimental-spoofping-fakeresponse-favicon)** <samp>`{type: string}`</samp> <samp>`{default: "undefined"}`</samp> : Spoofed Base64-encoded 64x64 png favicon
  - <span id='experimental-disconnectifnocontroller'></span>**[disconnectIfNoController](#user-content-experimental-disconnectifnocontroller)** <samp>`{type: object}`</samp>
    - <span id='experimental-disconnectifnocontroller-active'></span>**[active](#user-content-experimental-disconnectifnocontroller-active)** <samp>`{type: boolean}`</samp> : Whether to disconnect if noone is controlling the proxy disconnectIfNoController.delay seconds after a controller disconnects from the proxy while it isn't in queue
    - <span id='experimental-disconnectifnocontroller-delay'></span>**[delay](#user-content-experimental-disconnectifnocontroller-delay)** <samp>`{type: number}`</samp> <samp>`{default: 7}`</samp> : How long to wait (in seconds) after a controller disconnects from the proxy while it isn't in queue before disconnecting from the server
  - <span id='experimental-worlddownloader'></span>**[worldDownloader](#user-content-experimental-worlddownloader)** <samp>`{type: object}`</samp>
    - <span id='experimental-worlddownloader-active'></span>**[active](#user-content-experimental-worlddownloader-active)** <samp>`{type: boolean}`</samp> : **[Warning, Event Thread-Blocking!]** Whether to use the experimental world downloader
    - <span id='experimental-worlddownloader-compression'></span>**[compression](#user-content-experimental-worlddownloader-compression)** <samp>`{type: object}`</samp> : Settings for packet archive compression. Tweak with caution. The default options maximize memory usage for the fastest speed
      - <span id='experimental-worlddownloader-compression-level'></span>**[level](#user-content-experimental-worlddownloader-compression-level)** <samp>`{type: number}`</samp> <samp>`{default: 1}`</samp> : How much compression to apply between 1 and 9. Higher values result in better compression ratio at the expense of speed (**[Warning, Event Thread-Blocking!]**)
      - <span id='experimental-worlddownloader-compression-memlevel'></span>**[memLevel](#user-content-experimental-worlddownloader-compression-memlevel)** <samp>`{type: number}`</samp> <samp>`{default: 9}`</samp> : How much memory to allocate to the internal compression state between 1 and 9. Higher values result in better compression ratio and speed at the expense of memory usage
      - <span id='experimental-worlddownloader-compression-windowbits'></span>**[windowBits](#user-content-experimental-worlddownloader-compression-windowbits)** <samp>`{type: number}`</samp> <samp>`{default: 15}`</samp> : How much memory to allocate to the history buffer between 8 and 15. Higher values result in better compression ratio at the expense of memory usage
  - <span id='experimental-maxthreadpool'></span>**[maxThreadpool](#user-content-experimental-maxthreadpool)** <samp>`{type: object}`</samp>
    - <span id='experimental-maxthreadpool-active'></span>**[active](#user-content-experimental-maxthreadpool-active)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to set UV_THREADPOOL_SIZE to use all possible CPU logic cores

<span id='waitforcontrollerbeforeconnect'></span>**[waitForControllerBeforeConnect](#user-content-waitforcontrollerbeforeconnect)** <samp>`{type: boolean}`</samp> : Whether the proxy will wait for someone to take control before it connects to the server

<span id='notify'></span>**[notify](#user-content-notify)** <samp>`{type: object}`</samp> : Settings for what the proxy will send notifications about
  - <span id='notify-whenjoining'></span>**[whenJoining](#user-content-notify-whenjoining)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to send a toast notification and status webhook message when the proxy joins the server from queue
  - <span id='notify-whenbelowqueuethreshold'></span>**[whenBelowQueueThreshold](#user-content-notify-whenbelowqueuethreshold)** <samp>`{type: boolean}`</samp> <samp>`{default: true}`</samp> : Whether to send a toast notification and status webhook message when the proxy dips below position `queueThreshold` in queue
  - <span id='notify-whencontrolling'></span>**[whenControlling](#user-content-notify-whencontrolling)** <samp>`{type: boolean}`</samp> : Whether to send a status webhook message when a controller connects and disconnects from the proxy

<span id='nocligui'></span>**[noCliGui](#user-content-nocligui)** <samp>`{type: boolean}`</samp> : Whether to disable the cli gui

<span id='coordination'></span>**[coordination](#user-content-coordination)** <samp>`{type: object}`</samp> : Settings for coordinating multiple proxies
  - <span id='coordination-active'></span>**[active](#user-content-coordination-active)** <samp>`{type: boolean}`</samp> : Whether to use a [master config file and coordinator](https://github.com/Enchoseon/2based2wait/wiki/How-to-Proxy-Multiple-Accounts)
  - <span id='coordination-path'></span>**[path](#user-content-coordination-path)** <samp>`{type: string}`</samp> <samp>`{default: "./../"}`</samp> : Path to the folder where the shared master-config.json and coordinator.flag files should go