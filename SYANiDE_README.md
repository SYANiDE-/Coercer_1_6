(forked p0dalirius/Coercer > SYANiDE-/Coercer_1_6)
git clone git@github.com:SYANiDE-/Coercer_1_6.git ~/repos/Coercer_1_6
cd !:$
git reset --hard debc4c7 ## 1.6
checkout -b 1.6lock
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/Coercer.py -i
mv ~/repos/Coercer_1_6/coercer{,_1_6}
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/coercer_1_6/__main__.py -i
sed -re 's/from coercer\./from coercer_1_6\./g' ~/repos/Coercer_1_6/coercer_1_6/protocols/MS_{EFSR,FSRVP,DFSNM,RPRN}.py -i
sed -re 's/name = "coercer"/name = "coercer_1_6"/g' -e 's/coercer="coercer\./coercer_1_6="coercer_1_6\./g' ~/repos/Coercer_1_6/pyproject.toml -i
uv tool install .    ## installs coercer_1_6 on path
vim SYANiDE_README.md
git add *
git commit -m "Version locked Coercer 1.6"
git push origin 1.6lock
