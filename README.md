
# diffyaml
A simple tool for comparing yaml files
Shows changes containing the full path of nested parameters
## Install
clone repo
```bash
git clone https://github.com/datrav/diffyaml.git
```

set as executable: 
```bash
cd /diffyaml
chmod +x diffyaml.sh
```

## Usage

./diffyaml.sh someyamlfile1.yaml someyamlfile2.yaml

## Additional info

If you want to add it as part of command line tools, copy to /usr/local/bin:
```bash
cp diffyaml.sh /usr/local/bin/diffyaml
```

After that you can use it from command line in any place as:
```bash
diffyaml someyamlfile1.yaml someyamlfile2.yaml
```
