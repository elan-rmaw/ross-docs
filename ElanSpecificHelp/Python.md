# To download elan packages

## Cmd line
pip install artifacts-keyring
pip install elanpy[azure,db] --extra-index-url https://pkgs.dev.azure.com/elancapital/_packaging/ElanPyPI/pypi/simple/
pip install cobrapy --extra-index-url https://pkgs.dev.azure.com/elancapital/_packaging/ElanPyPI/pypi/simple/

## Requirements.txt
artifacts-keyring
--trusted-host pkgs.dev.azure.com
--extra-index-url https://pkgs.dev.azure.com/elancapital/_packaging/ElanPyPI/pypi/simple/
elanpy[azure,db]
cobrapy