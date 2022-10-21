
On Local Terminal 
```
export proj=iochainb
gh repo create mytestlab123/${proj} --public --description 'IO Chain'    # Create a public repo (cli or gui)

ignite s chain github.com/mytestlab123/$proj
cd $proj
git add -A
git commit -am "init"
git remote add origin https://github.com/mytestlab123/$proj.git
git remote -v
# git config --global --unset credential.helper
git push -u origin master
#ignite chain serve
```

on gitpod: https://github.com/ignite/gitpod
```
export proj=iochainb
ignite n chain publish github.com/mytestlab123/${proj}

export chainid=216
ignite n chain init ${chainid}
ignite n chain join ${chainid} --amount 95000000stake
ignite n request list ${chainid}
```

On validator
```
export chainid=216
ignite n chain init ${chainid}
ignite n chain join ${chainid} --amount 95000000stake
```

On coordinator
```
export chainid=216
ignite n request list ${chainid}

ignite n request approve ${chainid} 3,4,5,6
or
# ignite n request reject ${chainid} 7-10
ignite n request approve ${chainid} 11-12
ignite n request approve ${chainid} 3-8
```

Launch on validator and coordinator
```
export chainid=216
ignite n chain prepare $chainid
iochainbd start --home /home/ubuntu/spn/$chainid
```


For more docs: https://docs.ignite.com/network/introduction
old: https://github.com/tendermint/spn/blob/develop/docs/ignite_cli/coordinator.md
