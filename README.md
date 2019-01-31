# make_chroot_jail
sforkowane z https://github.com/pmenhart/make_chroot_jail

moje modyfikacje:
- usunąłęm linie związane z Ubuntu - powodowały błędy podczas uruchomienia skryptu
- do aplikacji dla Debiana dodałem **find** i **grep**

## o czym warto wiedzieć
- skrypt trzeba uruchamiać jako root
- skrypt w docelowej lokalizacji - w naszym przypadku folder z katalogami logów innych serwerów i urządzeń - utworzy katalogi z plikami niezbędnymi do działania chroot'a (m.in. bin, home, lib).

## instrukcja
- uruchamiać z konta root'a
- po skopiowaniu nadać uprawnienia do uruchomienia:
```bash
# chmod u+x make_chroot_jail.sh
```
- jako parametry podać: nazwę użytkownika, ścieżkę w której skrypt na utworzyć plik powłoki dla jail'a, ścieżkę do jaila (do niej będzie się automatycznie logował user)
- po zakończeniu działania skryptu należy ustawić hasło dla użytkownika:
```bash
# passwd nazwa_usera
```
- zrestartować sshd:
```bash
# /etc/init.d/ssh restart
```
