# EJP-T: Edged Judger Platform for Teachers 🍎

EJP-T is a specialized component of the Edged Judger Platform (EJP) designed to empower educators in the realm of coding education. Seamlessly integrated with the EJP ecosystem, EJP-T enables teachers to craft assignments, manage student grades, and even automate the grading process.

## Highlights 🌟

- **Craft Assignments**: Create coding assignments with custom criteria, deadlines, and point values.
- **Automated Grading**: Leverage automated grading scripts to evaluate student submissions.
- **Grade Management**: Keep track of student grades and progress with a simple and intuitive dashboard.
- **Cross-Component Integration**: Works in tandem with EJP-S (for Students) and EJP-BE (Server Program) to provide a comprehensive educational experience.

## Getting Started 📚

### Prerequisites

- Ensure that you have the main EJP system set up and running.
- Requires Linux OS (Windows & Mac support coming soon).

### Installation

1. Clone the EJP-T repository.
    ```bash
    git clone https://github.com/yourusername/ejp-t.git
    ```
2. Navigate to the cloned directory and run the installation script.
    ```bash
    cd ejp-t
    ./install.sh
    ```
3. Follow the on-screen prompts to complete the installation.

### Usage

1. Launch EJP-T from the command line:
    ```bash
    ejp-t [category] [command] [options] 
    ```
    Parameters
    * [category]: The category to which the command belongs (e.g., manage, workbook).
    * [command]: The specific action you want to perform (e.g., create, append, enroll).
    * [options]: Additional parameters or flags that modify the command. (e.g. -h(host), -l(location)).
    See [below](#Details) for more information about parameters.
2. Use the menu options to create new assignments, manage grades, or sync with EJP-S and EJP-BE.
3. For a list of all available commands and options, use:
    ```bash
    ejp-t help
    ```

## Contributing 🤝

We welcome contributions from the community! Feel free to fork the repository, make your changes, and submit a pull request. For more details, check out our [contribution guidelines](#).

## License 📄

EJP-T is part of the EJP project and follows the same MIT license.

## Details
* **Caching Options & Authentication**: Some `[options]` and authentication information can be saved locally to eliminate redundant input.
### manage
you can mange workbook(s).

``` bash
ejp-t manage [command] [options]
```

#### ```[command]```
0. ```create``` : create user(s) in certain host

    * ```-h``` : url of server (cached)
    * ```-u``` : a username to create
    * ```-p``` : password of a user to create
    * ```-l``` : path to `.csv` file with usernames and passwords (makes -u and -p optional)

    ```bash
    ejp-t manage create -u john1234 -p neo666
    ```
    or
    ```bash
    ejp-t manage create -h http://your.url.plz -l users_info.csv
    ```

1. ```enroll``` : enroll user(s) to workbook. with this command, able to assign workbook to students

    * ```-h``` : url of server (cached)
    * ```-u``` : name of a user to enroll
    * ```-r``` : name of workbook to enroll to (cached)
    * ```-l``` : path to .csv file with usernames and workbooks (makes -u and -r optional)

    ```bash
    ejp-t manage enroll -h http://your.url.plz -u john1234 -r swe2001_41
    ```
    or
    ```bash
    ejp-t manage enroll -l users_repo.csv
    ```

2. ```score``` : get score of user(s)

    * ```-h``` : url of server (cached)
    * ```-u``` : username to inspect (overrides -l)
    * ```-r``` : name of workbook to inspect (cached)
    * ```-p``` : name of problem to instpect. without this option, program will generate all scores about problems inside the workbook.
    * ```-l``` : path to store ```[workbook]-[problem].csv```file(e.g. ) which includes score of users. 

    ```bash
    ejp-t manage score -u john1234 -r swe2001_41 -p binary_tree
    ```
    or
    ```bash
    ejp-t manage score -p kmp_problem -l ./scores
    ```
    
3. ```list``` : get information of your workbook, problem, or testcases.
    * TBD.

### workbook
you manipulate workbook(s).

``` bash
ejp-t workbook [command] [options] 
```

#### ```[command]```
0. ```create``` : create workbook in certain host
1. ```append``` : append a problem to workbook or a testcase to problem
2. ```delete``` : delete workbook, problem or testcase