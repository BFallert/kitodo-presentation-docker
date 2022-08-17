# Kitodo.Presentation docker
Docker configuration for [Kitodo.Presentation](https://github.com/kitodo/kitodo-presentation).

## Kitodo.Presentation
Kitodo.Presentation is a feature-rich framework for building a METS- or IIIF-based digital library. It is part of the Kitodo Digital Library Suite.

More Information about Kitodo.Presentation can be found on the [official Git-Repository](https://github.com/kitodo/kitodo-presentation).

## Kitodo. Digital Library Modules
[Kitodo](https://github.com/kitodo) is an open source software suite intended to support mass digitization projects for cultural heritage institutions. Kitodo is widely used and cooperatively maintained by major German libraries and digitization service providers. The software implements international standards such as METS, MODS, ALTO, and other formats maintained by the Library of Congress. Kitodo consists of several independent modules serving different purposes such as controlling the digitization workflow, enriching descriptive and structural metadata, and presenting the results to the public in a modern and convenient way.

For more information, visit the [Kitodo homepage](https://www.kitodo.org). You can also follow Kitodo News on [Twitter](https://twitter.com/kitodo_org).

# Docker instructions
The Docker images were built by [Mannheim University Library](https://en.wikipedia.org/wiki/Mannheim_University_Library).

### Select branch
There are different [Branches](https://github.com/UB-Mannheim/kitodo-presentation-docker/branches) that serve to provide different installations. While the main-Branch offers always the newest presentation version, the others provide following versions:

| **Branch** 	| **dfg-viewer version** 	| **presentation version** 	| **base image** 	| **last commit** 	|
|:---:	|:---:	|:---:	|:---:	|:---:	|
| [main](https://github.com/UB-Mannheim/kitodo-presentation-docker) 	| - 	| [newest](https://github.com/kitodo/kitodo-presentation/releases) 	| [typo3-v10](https://github.com/csidirop/typo3-docker/tree/typo3-v10.x) 	| [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/UB-Mannheim/kitodo-presentation-docker/main?label=%20)](https://github.com/UB-Mannheim/kitodo-presentation-docker/commits/main) 	|
| [presentation-v4.x](https://github.com/UB-Mannheim/kitodo-presentation-docker/tree/presentation-v4.x) 	| - 	| [4.x](https://github.com/kitodo/kitodo-presentation/releases/tag/v4.0.1) 	| [typo3-v10](https://github.com/csidirop/typo3-docker/tree/typo3-v10.x) 	| [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/UB-Mannheim/kitodo-presentation-docker/presentation-v4.x?label=%20)](https://github.com/UB-Mannheim/kitodo-presentation-docker/commits/presentation-v4.x) 	|
| [presentation-v3.x](https://github.com/UB-Mannheim/kitodo-presentation-docker/tree/presentation-v3.x) 	| - 	| [3.x](https://github.com/kitodo/kitodo-presentation/releases/tag/v3.3.4) 	| [typo3-v9](https://github.com/csidirop/typo3-docker/tree/typo3-v9.x) 	| [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/UB-Mannheim/kitodo-presentation-docker/presentation-v3.x?label=%20)](https://github.com/UB-Mannheim/kitodo-presentation-docker/commits/presentation-v3.x) 	|
| [dfg-viewer-5.3](https://github.com/UB-Mannheim/kitodo-presentation-docker/tree/dfg-viewer-5.3) 	| [5.3](https://github.com/slub/dfg-viewer/releases/tag/v5.3.0) 	| [3.x](https://github.com/kitodo/kitodo-presentation/releases/tag/v3.3.4) 	| [typo3-v9](https://github.com/csidirop/typo3-docker/tree/typo3-v9.x) 	| [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/UB-Mannheim/kitodo-presentation-docker/dfg-viewer-5.3?label=%20)](https://github.com/UB-Mannheim/kitodo-presentation-docker/commits/dfg-viewer-5.3) 	|
| [dfg-viewer-5.3-ocr](https://github.com/UB-Mannheim/kitodo-presentation-docker/tree/dfg-viewer-5.3-ocr) 	| [5.3 with OCR-On-Demand](https://github.com/csidirop/dfg-viewer/tree/5.3-ocr-test) 	| [3.x](https://github.com/kitodo/kitodo-presentation/releases/tag/v3.3.4) 	| [typo3-v9](https://github.com/csidirop/typo3-docker/tree/typo3-v9.x) 	| [![GitHub last commit (branch)](https://img.shields.io/github/last-commit/UB-Mannheim/kitodo-presentation-docker/dfg-viewer-5.3-ocr?label=%20)](https://github.com/UB-Mannheim/kitodo-presentation-docker/commits/dfg-viewer-5.3-ocr) 	|

<!-- Table created with:  https://www.tablesgenerator.com/markdown_tables -->

### Checkout branch
    git checkout <branchname>

### Change credentials
Usernames and passwords for the database and typo3 backend are stored inside .env-File. It is of utmost importance to change these before productive use! Also the file should only be readable for root users.

### Run images:
    docker compose up

or  

    docker-compose up

### Ready:
Typo3 backend can be accessed at: http://localhost/typo3/


## Code and User Feedback
Please file your bug reports to [issues](https://github.com/UB-Mannheim/kitodo-presentation-docker/issues). Make sure that you are using the latest version of the software before sending a report.

This also means making sure that old docker caches/images/containers are not present **before** making a clean install:
- no old typo3-docker images are present: 
  - `docker images` should not show any typo3-docker image
  - otherwise remove it with `docker rmi <image-ids>`
- no presentation-containers present:
  - `docker container ls -a` should not show any kitodo-presentation container
  - run `docker compose down` to "stop containes and remove containers, networks, volumes, and images created by `docker compose up`"
  - run `docker rm <container_ID/NAME>` if anything kitodo-presentation related still present
- build without using cached layers:
  - `docker compose build --no-cache`
