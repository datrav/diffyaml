
# diffyaml
A simple tool for comparing yaml files
Shows changes containing the full path of nested parameters
## Preinstall
Install **yq** tool if non installed [https://github.com/mikefarah/yq](https://github.com/mikefarah/yq?tab=readme-ov-file#install)
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

## Example

file1.yaml
```yaml
version: 2.1

# Define the jobs we want to run for this project
jobs:
  build:
    docker:
      - image: cimg/base:2023.03
    steps:
      - checkout
      - run: echo "this is the build job"
  test:
    docker:
      - image: cimg/base:2023.03
    steps:
      - checkout
      - run: echo "this is the test job"

# Orchestrate our job run sequence
workflows:
  build_and_test:
    jobs:
      - build
      - test

```

file2.yaml
```yaml
version: 2.1

# Define the jobs we want to run for this project
jobs:
  build:
    docker:
      - image: cimg/base:2023.03
    steps:
      - checkout
      - run: echo "this is the build job"
  test:
    docker:
      - image: cimg/base:2023.04
    steps:
      - checkout
      - run: echo "this is the test job"

# Orchestrate our job run sequence
workflows:
  build_and_test:
    jobs:
      - build
      - test
```
Run:
```bash
diffyaml file1.yaml file2.yaml
```
Result:
```yaml
jobs:
  test:
    docker:
      - image: cimg/base:2023.04
```
