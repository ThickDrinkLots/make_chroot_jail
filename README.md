# make_chroot_jail
sforkowane z https://github.com/pmenhart/make_chroot_jail

### moje modyfikacje:
- usunąłęm linie związane z Ubuntu - powodowały błędy podczas uruchomienia skryptu
- usunąłem zbędne aplikacje: **rm**, **rmdir**, **cp**, **mkdir**, **mv**, **nano**
- do aplikacji dla Debiana dodałem **find**, **grep**, **vim**

### o czym warto wiedzieć
- rozwiązanie niestety pozwala na wykonanie exploita polegającego na tym, że inny user dostanie uprawnienia root'a. Żeby do tego doszło user A poza chrootem musi znać hasło usera B, który ma dostęp do chroot'a.   
- skrypt trzeba uruchamiać jako root
- skrypt w docelowej lokalizacji - w naszym przypadku folder z katalogami logów innych serwerów i urządzeń - utworzy katalogi z plikami niezbędnymi do działania chroot'a (m.in. bin, home, lib).

### instrukcja
- uruchamiać z konta root'a
- po skopiowaniu nadać uprawnienia do uruchomienia:
```bash
# chmod u+x make_chroot_jail.sh
```
- jako parametry podać: nazwę użytkownika, ścieżkę w której skrypt na utworzyć plik powłoki dla jail'a, ścieżkę do jaila (do niej będzie się automatycznie logował user), np.:
```bash
# ./make_chroot_jail.sh nazwa_usera /bin/chroot-shell /var/log/alienvault/devices
```
- po zakończeniu działania skryptu należy ustawić hasło dla użytkownika:
```bash
# passwd nazwa_usera
```
- zrestartować sshd:
```bash
# /etc/init.d/ssh restart
```
