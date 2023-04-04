#### journald is the daemon from systemd that collects the logs from various log sources like syslog. journalctl is the command line tool that lets you interact with the journal logs. The default location of journald logs is /var/log/journal directory. If you just type journalctl in the terminal, it will show the journal logs in chronological order.

```
[tuttu@fedora ~]$ journalctl
Jan 08 22:12:42 fedora systemd-resolved[722]: Clock change detected. Flushing caches.
Jan 08 22:12:42 fedora systemd-journald[571]: Time jumped backwards, rotating.
Jan 08 22:12:42 fedora systemd-timedated[16849]: Changed local time to Sun 2023-01-08 11:42:42 >
Jan 08 22:11:42 fedora systemd-resolved[722]: Clock change detected. Flushing caches.
Jan 08 22:11:42 fedora systemd-journald[571]: Time jumped backwards, rotating.
Jan 08 22:11:42 fedora systemd-timedated[16849]: Changed local time to Sun 2023-01-08 11:41:42 >
Jan 08 22:10:42 fedora systemd-resolved[722]: Clock change detected. Flushing caches.
Jan 08 22:10:42 fedora systemd-journald[571]: Time jumped backwards, rotating.
Jan 08 22:10:42 fedora systemd-timedated[16849]: Changed local time to Sun 2023-01-08 11:40:42 >
Jan 08 22:09:42 fedora systemd-timedated[16849]: Changed local time to Sun 2023-01-08 11:39:42 >
Jan 08 22:09:42 fedora systemd-journald[571]: Time jumped backwards, rotating.
```

#### If you want to see the recent logs first, you can display the journal logs in reverse order with the option -r:

```
[tuttu@fedora ~]$ journalctl -r
Apr 04 16:38:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:38:30.672] [   ] [d>
Apr 04 16:37:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:37:30.623] [   ] [d>
Apr 04 16:36:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:36:30.625] [   ] [d>
Apr 04 16:36:16 fedora google-chrome.desktop[4127]: Fontconfig error: Cannot load default confi>
Apr 04 16:35:54 fedora wpa_supplicant[1050]: wlp1s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-3>
Apr 04 16:35:41 fedora google-chrome.desktop[4127]: Fontconfig error: Cannot load default confi>
Apr 04 16:35:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:35:30.627] [   ] [d>
Apr 04 16:34:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:34:30.625] [   ] [d>
Apr 04 16:33:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:33:30.640] [   ] [d>
Apr 04 16:32:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:32:30.683] [   ] [d>
Apr 04 16:31:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:31:30.640] [   ] [d>
Apr 04 16:30:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:30:30.672] [   ] [d>
Apr 04 16:29:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:29:30.640] [   ] [d>
```

#### if you want to see the logs in real time, you can use the -f option of journalctl command:

```
[tuttu@fedora ~]$ journalctl -f
Apr 04 16:33:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:33:30.640] [   ] [debug] autosave no need
Apr 04 16:34:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:34:30.625] [   ] [debug] autosave no need
Apr 04 16:35:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:35:30.627] [   ] [debug] autosave no need
Apr 04 16:35:41 fedora google-chrome.desktop[4127]: Fontconfig error: Cannot load default config file: No such file: (null)
Apr 04 16:35:54 fedora wpa_supplicant[1050]: wlp1s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-30 noise=9999 txrate=270000
```

#### If you just want to see Linux kernel logs, you can use the option -k

```
tuttu@fedora ~]$ journalctl -k
Apr 04 12:16:53 fedora kernel: microcode: microcode updated early to revision 0xa4, date = 2022>
Apr 04 12:16:53 fedora kernel: Linux version 6.2.8-200.fc37.x86_64 (mockbuild@bkernel01.iad2.fe>
Apr 04 12:16:53 fedora kernel: Command line: BOOT_IMAGE=(hd0,gpt5)/vmlinuz-6.2.8-200.fc37.x86_6>
Apr 04 12:16:53 fedora kernel: x86/split lock detection: #AC: crashing the kernel on kernel spl>
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point reg>
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x020: 'AVX-512 opmask'
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x040: 'AVX-512 Hi256'
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x080: 'AVX-512 ZMM_Hi256'
Apr 04 12:16:53 fedora kernel: x86/fpu: Supporting XSAVE feature 0x200: 'Protection Keys User r>
Apr 04 12:16:53 fedora kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Apr 04 12:16:53 fedora kernel: x86/fpu: xstate_offset[5]:  832, xstate_sizes[5]:   64
Apr 04 12:16:53 fedora kernel: x86/fpu: xstate_offset[6]:  896, xstate_sizes[6]:  512
Apr 04 12:16:53 fedora kernel: x86/fpu: xstate_offset[7]: 1408, xstate_sizes[7]: 1024
Apr 04 12:16:53 fedora kernel: x86/fpu: xstate_offset[9]: 2432, xstate_sizes[9]:    8
Apr 04 12:16:53 fedora kernel: x86/fpu: Enabled xstate features 0x2e7, context size is 2440 byt>
Apr 04 12:16:53 fedora kernel: signal: max sigframe size: 3632
```

####  You can list all the boot sessions with --list-boots flag.

```
[tuttu@fedora ~]$ journalctl --list-boots
IDX BOOT ID                          FIRST ENTRY                 LAST ENTRY                 
-58 8a908420d5d64224868e5a068247d4d7 Sun 2023-01-08 22:12:42 IST Sun 2023-01-08 22:02:26 IST
-57 63a777c0e2ba43cd8cc13105d40d094c Sun 2023-01-22 00:24:46 IST Sun 2023-01-22 12:22:04 IST
-56 9ef6c113fd4c4936b17e02cb9d9ae9df Thu 2023-02-02 04:21:00 IST Thu 2023-02-02 20:22:28 IST
-55 a53b856acd6c412baff06773dfe30cea Fri 2023-02-03 09:58:15 IST Fri 2023-02-03 19:53:26 IST
-54 42bea2fde37340e3b23fbfc7cd71c014 Fri 2023-02-03 19:53:37 IST Fri 2023-02-03 19:55:18 IST
-53 750b1e69cc3f4d48b5cc800825435abf Sun 2023-02-05 12:39:40 IST Sun 2023-02-05 12:55:15 IST
```

#### Boot session 0 is the current boot sessions. Boot session -1 is the last booted session and so on. Analysing logs from a speicific boot session

```
[tuttu@fedora ~]$ journalctl -b -53 
Feb 05 12:39:40 fedora kernel: microcode: microcode updated early to revision 0xa4, date = 2022>
Feb 05 12:39:40 fedora kernel: Linux version 6.1.8-200.fc37.x86_64 (mockbuild@bkernel01.iad2.fe>
Feb 05 12:39:40 fedora kernel: Command line: BOOT_IMAGE=(hd0,gpt5)/vmlinuz-6.1.8-200.fc37.x86_6>
Feb 05 12:39:40 fedora kernel: x86/split lock detection: #AC: crashing the kernel on kernel spl>
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point reg>
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x020: 'AVX-512 opmask'
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x040: 'AVX-512 Hi256'
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x080: 'AVX-512 ZMM_Hi256'
Feb 05 12:39:40 fedora kernel: x86/fpu: Supporting XSAVE feature 0x200: 'Protection Keys User r>
Feb 05 12:39:40 fedora kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Feb 05 12:39:40 fedora kernel: x86/fpu: xstate_offset[5]:  832, xstate_sizes[5]:   64
```

#### Using journalctl -xe for viewing last few logs

```
[tuttu@fedora ~]$ journalctl -xe 
Apr 04 16:29:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:29:30.640] [   ] [d>
Apr 04 16:30:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:30:30.672] [   ] [d>
Apr 04 16:31:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:31:30.640] [   ] [d>
Apr 04 16:32:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:32:30.683] [   ] [d>
Apr 04 16:33:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:33:30.640] [   ] [d>
Apr 04 16:34:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:34:30.625] [   ] [d>
Apr 04 16:35:30 fedora cherrytree_cherrytree.desktop[15761]: [2023-04-04 16:35:30.627] [   ] [d>
Apr 04 16:35:41 fedora google-chrome.desktop[4127]: Fontconfig error: Cannot load default confi>
Apr 04 16:35:54 fedora wpa_supplicant[1050]: wlp1s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-3>
Apr 04 16:36:16 fedora google-chrome.desktop[4127]: Fontconfig error: Cannot load default confi>
```

#### To show all the errors in the current session, you can use:

```
[tuttu@fedora ~]$ journalctl -p 3 -xb
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.FN00]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.FAN0]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.TZ00]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora systemd[1]: bpf-lsm: Failed to load BPF object: No such process
Apr 04 12:16:55 fedora systemd[1]: bpf-lsm: Failed to load BPF object: No such process
```

#### You can also use other priority level to get debug, or warning or even critical level logs. 

```
[tuttu@fedora ~]$ journalctl -p crit -b
-- No entries --

[tuttu@fedora ~]$ journalctl -p err -b
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.FN00]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.FAN0]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora kernel: ACPI BIOS Error (bug): Failure creating named object [\_TZ.TZ00]>
Apr 04 12:16:53 fedora kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20221>
Apr 04 12:16:53 fedora systemd[1]: bpf-lsm: Failed to load BPF object: No such process
Apr 04 12:16:55 fedora systemd[1]: bpf-lsm: Failed to load BPF object: No such process
Apr 04 12:16:55 fedora systemd-gpt-auto-generator[533]: Failed to dissect: Permission denied
Apr 04 12:16:55 fedora (sd-executor)[516]: /usr/lib/systemd/system-generators/systemd-gpt-auto->
Apr 04 12:16:57 fedora bluetoothd[799]: src/plugin.c:plugin_init() Failed to init vcp plugin
Apr 04 12:16:57 fedora bluetoothd[799]: src/plugin.c:plugin_init() Failed to init mcp plugin
Apr 04 12:16:57 fedora bluetoothd[799]: src/plugin.c:plugin_init() Failed to init bap plugin

```

#### You can check how much disk space the journal logs are taking with this journalctl command:

```
[tuttu@fedora ~]$ journalctl --disk-usage
Archived and active journals take up 679.9M in the file system.
```

```
-p 3 : filter logs for priority 3 (which is error)
-x : provides additional information on the log (if available)
b : since last boot (which is the current session)
-e: Jump to the end of the journal logs
-x: Show extra information on the log entries (if available)
```
