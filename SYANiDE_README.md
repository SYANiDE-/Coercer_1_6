Version lock 1.6 and make UV install the binary under a different name and context.  1.6 can coerce WebDav to send HTTP/S authentications,
Good for SMB Signing scenarios because signing can't be used/requested in HTTP/S scenarios.

Why am I doing this?  Yeah I read https://github.com/p0dalirius/Coercer issue #40.  But for the life of me, even 2.4.3, I just can't get the same behavior/results.

1.6 seems to be the shit for coercing WebDav (http/s) authentications.  2.4.3 just won't.  Even if issue #40's screenshots show it can.  Not sure why.  Just need it to work, and so version-locked Coerce_1_6 is (re)born

Fuck it I'm a gremlin
```
(forked p0dalirius/Coercer > SYANiDE-/Coercer_1_6)
git clone git@github.com:SYANiDE-/Coercer_1_6.git ~/repos/Coercer_1_6
cd !:$
git reset --hard debc4c7 ## 1.6
mv ~/repos/Coercer_1_6/coercer{,_1_6}
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/Coercer.py -i
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/coercer_1_6/__main__.py -i
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/coercer_1_6/protocols/MS_{EFSR,FSRVP,DFSNM,RPRN}.py -i
sed -re 's/name = "coercer"/name = "coercer_1_6"/g' -e 's/coercer="coercer\./coercer_1_6="coercer_1_6\./g' ~/repos/Coercer_1_6/pyproject.toml -i
uv tool install .    ## installs coercer_1_6 on path
vim SYANiDE_README.md
git add *
git commit -m "Version locked Coercer 1.6"
git push origin master --force
```
