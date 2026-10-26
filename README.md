# Uxen/zf1-future — miroir de Shardj/zf1-future

Copie de sauvegarde du dépôt [Shardj/zf1-future](https://github.com/Shardj/zf1-future), le fork de
Zend Framework 1 qu'easyReco installe par Composer (`shardj/zf1-future`, ticket DEV-13224). Elle
garantit qu'une version épinglée reste installable même si le dépôt amont disparaît ou réécrit son
historique.

- La branche `master` et les tags `release-*` sont ceux de l'amont, poussés tels quels, sans
  modification locale. Les adaptations d'easyReco restent dans ses patches Composer
  (`patches/zf1-future/` du dépôt easyreco), pas ici.
- La branche `uxen` (celle-ci, branche par défaut) ne porte que ce README et le workflow de
  synchronisation : elle n'a pas de `composer.json`, Composer l'ignore.
- `.github/workflows/sync-upstream.yml` rejoue chaque nuit `git fetch upstream` puis pousse
  `master` et les tags. Un push refusé (historique amont réécrit, tag déplacé) fait échouer le
  job au lieu d'écraser la sauvegarde : c'est voulu, un humain tranche.

Côté easyReco, `composer.json` déclare ce dépôt en `repositories` (type `git`, URL https publique,
aucune clé requise) et épingle une version exacte ; le nom du paquet reste `shardj/zf1-future`,
celui du `composer.json` amont.

Synchronisation à la main :

```bash
git fetch upstream --tags
git push origin refs/remotes/upstream/master:refs/heads/master
git push origin --tags
```

(`upstream` = `https://github.com/Shardj/zf1-future.git`.)
