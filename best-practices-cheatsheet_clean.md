<span class="header">Contents </span>

-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Organization-of-files-and-folders"
    data-toc-modified-id="Organization-of-files-and-folders-1"><span
    class="toc-item-num">1  </span>Organization of files and folders</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Driver-script-(usually-Bash)"
    data-toc-modified-id="Driver-script-(usually-Bash)-2"><span
    class="toc-item-num">2  </span>Driver script (usually Bash)</a>
    -   <a
        href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Alternative:-Notebook"
        data-toc-modified-id="Alternative:-Notebook-2.1"><span
        class="toc-item-num">2.1  </span>Alternative: Notebook</a>
    -   <a
        href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Modern-alternative:-Workflow-management-system"
        data-toc-modified-id="Modern-alternative:-Workflow-management-system-2.2"><span
        class="toc-item-num">2.2  </span>Modern alternative: Workflow management
        system</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Code-development"
    data-toc-modified-id="Code-development-3"><span
    class="toc-item-num">3  </span>Code development</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Version-control-system"
    data-toc-modified-id="Version-control-system-4"><span
    class="toc-item-num">4  </span>Version control system</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-data-management"
    data-toc-modified-id="Basic-data-management-5"><span
    class="toc-item-num">5  </span>Basic data management</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-project-management"
    data-toc-modified-id="Basic-project-management-6"><span
    class="toc-item-num">6  </span>Basic project management</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Collaborating-on-computational-projects"
    data-toc-modified-id="Collaborating-on-computational-projects-7"><span
    class="toc-item-num">7  </span>Collaborating on computational
    projects</a>
    -   <a
        href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-manuscript-management"
        data-toc-modified-id="Basic-manuscript-management-7.1"><span
        class="toc-item-num">7.1  </span>Basic manuscript management</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Cyber-security:-passwords-and-encryption"
    data-toc-modified-id="Cyber-security:-passwords-and-encryption-8"><span
    class="toc-item-num">8  </span>Cyber security: passwords and
    encryption</a>
-   <a
    href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Beware-of-..."
    data-toc-modified-id="Beware-of-...-9"><span
    class="toc-item-num">9  </span>Beware of ...</a>

# Short guide to scientific computational projects

**Core guiding principle:** Someone unfamiliar with your project
(including you, some time later) should be able to look at your files,
understand what you did and why, and easily repeat it.

**Murphy’s Law for computational projects:** For anything you do, you
will probably have to repeat it again later (new data, new parameters,
fixing bugs).

**General idea:** Breaking a lengthy workflow into pieces makes it
easier to understand, share, describe, and modify. Make your project
modular, and the modules transparent and reproducible. This is important
**for you and for others**.

**Fun fact:** Sticking to good practices in a scientific computational
project can save you a lot of time later, and make you (and others) a
happier person.

## <span id="Organization-of-files-and-folders-1" class="toc-mod-link"></span><span class="toc-item-num">1  </span>Organization of files and folders<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Organization-of-files-and-folders"
class="anchor-link">¶</a>

Stick to a standardized and self-explanatory directory structure.
Essential text files like scripts and notes should be managed by a
version control system (Git). Suggested organization:

Suggested project structure for computational projects

(compare to [Noble
2009](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424#s3))

Note: This structure is a suggestion, which has proven useful. You can
use it as a starting point.

All projects live in a `workspace` or `projects` directory. Each project
gets its own directory, `project_name`. The contents should be **as
standardized as possible**:

-   A project-level `README.md` is usually the first thing someone reads
    (project purpose, how to reproduce, dependencies)
-   `notes.txt` or better `notes.md` (project notes/lab notebook):
    -   Chronologically organized; also useful for meetings/progress
        reports
    -   Simple text file is often good enough, but can be another format
-   `requirements.txt` or better `environment.yml`: for conda- or
    pip-installed packages, do `conda env export > environment.yml` to
    define the current environment in terms of all packages and their
    versions
    ([docs.conda.io](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html))
-   `doc/`: has subfolders like `doc/manuscript1/` for
    manuscript-related content, like final figures
-   `bin/`: contains all code required to reproduce the project
    -   there may be multiple `bin/` folders that reside in
        experiment-specific subfolders (if this is more convenient)
-   Sometimes there might be a `src/` folder for source code (in this
    case, `bin/` contains actual
    [binaries](https://unix.stackexchange.com/a/372875))
-   `data/` contains raw input data; possible naming schemes:
    -   E.g. `data/sample1/`, `data/sample2/` etc. (logical
        organization)
    -   Or `data/20180130/`, `data/20180131/` etc. (chronological
        organization)
-   `runall.sh`: some people use a single driver script that runs all
    other scripts and generates all results; this can be useful, but
    less flexible than separate experiments with their own driver
    scripts
-   If Git is used: use `.gitignore` file to place [only relevant
    files](https://stackoverflow.com/a/9227991/) (`*.py`, `*.txt`,
    `*.sh`, `*.R`, `*.md`, ...) under version control
-   Further reading:
    -   [Noble
        2009](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1000424).
        A Quick Guide to Organizing Computational Biology Projects. PLOS
        Computational Biology.
    -   [biostars.org](https://www.biostars.org/p/821/)

Additional tips:

-   Move finished projects from the `workspace` (or `project`) directory
    to the `archive` directory
-   Create additional directories in the `doc` directory, e.g.
    `planning` for notes/objectives/initial drafts that you collect in
    the first weeks of a projects

## <span id="Driver-script-(usually-Bash)-2" class="toc-mod-link"></span><span class="toc-item-num">2  </span>Driver script (usually Bash)<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Driver-script-(usually-Bash)"
class="anchor-link">¶</a>

-   Often includes calls to shell commands, Python scripts, R scripts
    (using [Rscript](https://stackoverflow.com/a/18306656/), also see
    [Rstudio
    docs](https://support.posit.co/hc/en-us/articles/218012917-How-to-run-R-scripts-from-the-command-line))
    and precompiled programs
-   **Automates every data processing step** like creating the required
    directory structure
-   **Records every performed operation** (beware of manual editing of
    output files)
-   Contains **informative comments** that explain what's going on
-   Contains **all relevant information** like file and directory names
    and passes them as arguments to other scripts/programs
-   Stores paths and constants as **variables in a separate section** in
    the beginning ("variable section"). Think of it as a configuration
    section. This makes the code structure clearer, and code
    modifications easier.
-   Uses **relative paths** (project folder can be transferred to
    another location and still works)
-   Uses `set -euxo pipefail` options (or some of them) for [safer
    scripting](https://vaneyckt.io/posts/safer_bash_scripts_with_set_euxo_pipefail/)
-   **Checks data consistency/plausibility** frequently to make sure
    that nothing unexpected happened (and the results make sense)
-   You can use
    `if (output_file does not exist), then <perform operation>`
    constructs to **easily repeat parts** of the experiment (after
    deletion of the respective output files)

**The environment** in which the driver script operates should be
clearly defined (required tools/databases and their versions), e.g. via

-   `environment.yml` for [conda
    environments](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/04-sharing-environments/index.html),
-   `renv.lock` for [R
    environments](https://rstudio.github.io/renv/articles/renv.html)
    ([renv](https://github.com/rstudio/renv),
    [reproducibility.rocks](https://reproducibility.rocks/materials/day3/01-renv/),
    [Siraji & Rahman
    2023](https://pmc.ncbi.nlm.nih.gov/articles/PMC10969410/)),
-   `uv.lock` for Python-only projects
    ([uv](https://github.com/astral-sh/uv),
    [realpython.com](https://realpython.com/python-uv/),
    [aeturrell.github.io](https://aeturrell.github.io/coding-for-economists/wrkflow-rap.html))
-   Make sure that everything actually works if run in the defined
    environment! The best approach is to reproduce the entire workflow
    from scratch on another machine (or virtual machine).
-   A powerful but also more complex approach which completely solves
    the "it works on my machine" problem and is still cheaper than a
    full-fledged VM is containerization
    ([Docker](https://docs.docker.com/get-started/),
    [Apptainer](https://apptainer.org/docs/user/latest/))

### <span id="Alternative:-Notebook-2.1" class="toc-mod-link"></span><span class="toc-item-num">2.1  </span>Alternative: Notebook<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Alternative:-Notebook"
class="anchor-link">¶</a>

-   Jupyter notebooks or [R
    notebooks](https://bookdown.org/yihui/rmarkdown/notebook.html) (R
    notebooks have [some
    advantages](https://minimaxir.com/2017/06/r-notebooks/), including
    easier version control; Jupyter notebooks have other advantages, and
    can be enhanced by
    [plugins](https://jupyterlab.readthedocs.io/en/stable/user/extensions.html))
-   Notebooks combine code, explanatory text and results. They are great
    for data exploration, demonstration and teaching purposes
    ([nature.com](https://www.nature.com/articles/d41586-018-07196-1),
    [reddit](https://www.reddit.com/r/Python/comments/ejgyfe/do_professional_data_analyst_use_jupyter_or_do/)),
    but less suitable for code development or complex workflows
    involving different programs
-   Notebooks are a useful data science tool if used properly: should be
    well named, clearly structured, informatively commented
-   Great for sharing reproducible workflows and results with other
    people
-   [VS
    Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
    became a very useful and versatile environment for working with
    notebooks, with many additional plugins

### <span id="Modern-alternative:-Workflow-management-system-2.2" class="toc-mod-link"></span><span class="toc-item-num">2.2  </span>Modern alternative: Workflow management system<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Modern-alternative:-Workflow-management-system"
class="anchor-link">¶</a>

-   “Scripting usually suffices for one-off tasks and when working out
    the pipeline itself. The tipping point comes when you need to run
    the same workflow over and over again, or if the data are likely to
    be published.”
    ([nature.com](https://www.nature.com/articles/d41586-019-02619-z)) →
    consider using a workflow management system like
    [Snakemake](https://snakemake.readthedocs.io/en/stable/tutorial/tutorial.html)
    ([GitHub](https://github.com/snakemake/snakemake)),
    [Nextflow](https://www.nextflow.io/docs/latest/getstarted.html)
    ([GitHub](https://github.com/nextflow-io/nextflow)) or
    [Galaxy](https://galaxyproject.org/) ([The Galaxy Community
    2024](https://academic.oup.com/nar/article/52/W1/W83/7676834))
-   This breaks the analysis down into tasks or processes and link them
    together in a pipeline, with defined inputs and outputs
-   Such tools are becoming increasingly popular, and you should
    seriously consider using them
-   Further information:
    -   [Wratten et al.
        2021](https://www.nature.com/articles/s41592-021-01254-9).
        Reproducible, scalable, and shareable analysis pipelines with
        bioinformatics workflow managers.
        ([GitHub](https://github.com/GoekeLab/bioinformatics-workflows))
    -   "Introducing snakemake" by Edinburgh Genomics Training, 2020
        ([YouTube](https://www.youtube.com/watch?v=NNPBDOBHlxo))
    -   "Nextflow Training Workshop - July 2020 - Day 1" by Nextflow,
        2020 ([YouTube](https://www.youtube.com/watch?v=8_i8Tn335X0))

## <span id="Code-development-3" class="toc-mod-link"></span><span class="toc-item-num">3  </span>Code development<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Code-development"
class="anchor-link">¶</a>

-   **Developing code** should always start with **clear
    specifications** of what the code is supposed to do when ready, in
    terms of input and output. Put it in a comment section in the
    beginning.
-   Start development with **pseudocode** (or flowchart) that outlines
    the script logic. This is very helpful even for simple scripts.
    Translate the pseudocode into code step by step.
-   Provide **skeletal documentation** (basic usage information) even
    for short scripts
    ([realpython.com](https://realpython.com/documenting-python-code/),
    [google.github.io](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings)).
    **Simple examples** are very helpful.
    -   You can add them to built-in documentation, e.g. the module
        docstring ([Biopython
        example](https://github.com/biopython/biopython/blob/master/Bio/SeqRecord.py)),
        which can be converted to external documentation ([Biopython
        example](https://biopython.org/docs/latest/api/Bio.SeqRecord.html))
    -   You can also provide additional documentation, e.g. a
        `README.md` file ([example](https://github.com/voutcn/megahit))
        or a Wiki
        ([example](https://github.com/biobakery/MetaPhlAn/wiki/MetaPhlAn-4))
-   Provide **test cases** to demonstrate how the script is used and
    that it works as expected
    -   One simple approach to testing are print-and-compare tests,
        whereby you provide some test data that allows to verify that
        the script output is correct
    -   A more advanced approach are unit tests and the
        [pytest](https://docs.pytest.org/) framework
        ([realpython.com](https://realpython.com/python-testing/)); in
        this case, you write an additional Python file with test cases
        ([Biopython
        example](https://github.com/biopython/biopython/blob/master/Tests/pairwise2_testCases.py))
-   The same applies to functions:
    -   **Every function/method** should have a **docstring** that
        briefly describes the arguments and the return value
        ([realpython.com](https://realpython.com/documenting-python-code/#documenting-your-python-code-base-using-docstrings))
    -   Python [doctests](https://pymotw.com/3/doctest/) are simple test
        cases in docstrings, which are useful as basic usage examples
        and documentation
    -   Python [type hints](https://stackoverflow.com/a/32558710/) can
        help in development, documentation and debugging
-   Adopt **iterative and incremental development**: start with a
    minimalistic working version, keep changes small, test frequently.
    -   Can include empty functions, that specify what they do in the
        docstring and consist of a `pass` statement.
-   Write modular code, i.e., **short, single-purpose
    functions/scripts** with clearly defined inputs and outputs →
    readable, reusable, and testable; avoid “swiss-army-knife” design
    that does many different things
-   Scripts should **break immediately if something is wrong**: check
    consistency whenever possible (Python: `assert` for
    development/testing), e.g. input arguments should have the expected
    type and make sense, files shouldn't be empty, results should be
    consistent, etc.
    -   Professional production-grade code would use
        `if ... raise ValueError(...)` or the more powerful but also
        more complex [Pydantic](https://realpython.com/python-pydantic/)
        library for validation, but for our purposes, `assert` is good
        enough in most cases
-   **Don't Repeat Yourself**: Code duplication is usually a sign of
    poor program design; copying/pasting code is cheap for solving the
    immediate problem, but [dangerous medium/long
    term](https://stackoverflow.com/questions/2490884/why-is-copy-and-paste-of-code-dangerous)
-   Look for **well-maintained libraries** that help you do what you’re
    trying to do *before* writing your own code
-   Learn to effectively use **AI coding assistants**. This is a new
    skillset which is become increasingly important and takes time to
    learn. You'll need to find out when it's helpful and when it's
    risky; generally, always verify output, and don't submit code you
    don't understand.
-   Stick to **best practices** for writing code:
    -   Respect language-specific **style guidelines** (Python:
        [PEP8](https://realpython.com/python-pep8/), [Google style
        guide](https://google.github.io/styleguide/pyguide.html))
    -   Use **linters** and **formatters** (Python:
        [Ruff](https://docs.astral.sh/ruff/), or if you can't use Ruff,
        then
        [Flake8](https://realpython.com/python-code-quality/#linters),
        [pylint](https://www.reddit.com/r/Python/comments/82hgzm/any_advantages_of_flake8_over_pylint/),
        [Black](https://black.readthedocs.io/en/stable/))
    -   Use **type checkers** (Python:
        [MyPy](https://mypy.readthedocs.io/en/stable/))
    -   Many IDEs provide built-in code analysis (e.g.
        [Spyder](https://stackoverflow.com/a/51467284/), [VS
        Code](https://code.visualstudio.com/docs/python/linting),
        [PyCharm](https://www.jetbrains.com/help/pycharm/configuring-third-party-tools.html#pylint-configure))
    -   Running code checkers and testing can be annoying, but better
        than [retracting a publication because of a
        bug](https://arstechnica.com/information-technology/2019/10/chemists-discover-cross-platform-python-scripts-not-so-cross-platform/)
        ([ivory
        blog](http://ivory.idyll.org/blog/automated-testing-and-research-software.html))
-   Always assume that you might have to share your code later with
    other people ([ivory
    blog](http://ivory.idyll.org/blog/2015-how-should-we-think-about-research-software.html))
-   Get to know your
    [IDE](https://www.datacamp.com/community/tutorials/data-science-python-ide)
    to improve productivity (e.g. Spyder, VS Code, PyCharm; Jupyter +
    plugins is great for data analysis, but not necessarily for code
    development)

  

<a href="https://xkcd.com/1513/" class="img-caption">Style guide
(xkcd.com/1513)</a>

## <span id="Version-control-system-4" class="toc-mod-link"></span><span class="toc-item-num">4  </span>Version control system<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Version-control-system"
class="anchor-link">¶</a>

A version control system (VCS) stores snapshots of a project’s files in
a repository. This has important advantages:

1.  **Free and easy backup of all your precious scripts and project
    notes**
2.  Keeps track of **changes** (versions/tags), so you don’t need file
    names like `script_v1.py`, `script_v1.2.py`, `script_final.py`,
    `script_really_final.py`, `script_absolutely_final.py` etc.
3.  Allows code **modifications** (branches) without breaking existing
    functionality, facilitates conflict resolution

In which cases should you use a VCS?

-   If you **collaborate with others**, you definitely want VCS
-   If you work on a **larger codebase**, you definitely want VCS
-   If you want to **preserve and re-use** your code later, you
    definitely want VCS
-   A VCS is intended for use with text files that are essential to
    reproducing your project:
    -   Most importantly, all data processing scripts (e.g. Python, R,
        Bash), scientific notes and related text files. **Put them all
        under version control.**
    -   Large and/or binary files are NOT intended for use with VCS:
        -   Raw data and, in general, large files and binary files
            (should be backed up elsewhere)
        -   Automatically generated files like intermediate and result
            files (can be re-calculated if required)
-   Further reading:
    -   [Blischak et al.
        2016](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).
        A Quick Introduction to Version Control with Git and GitHub.
    -   [Perez-Riverol et al.
        2016](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004947).
        Ten Simple Rules for Taking Advantage of Git and GitHub.
-   [Stackoverflow](https://stackoverflow.com/questions/2712421/r-and-version-control-for-the-solo-data-analyst),
    [Datascience-Stackexchange](https://datascience.stackexchange.com/questions/5178/how-to-deal-with-version-control-of-large-amounts-of-binary-data),
    [Bioinformatics-Stackexchange](https://bioinformatics.stackexchange.com/questions/112/how-to-version-the-code-and-the-data-during-the-analysis)

Simply put: Whenever writing code that you intend to use more than once,
you should be using a VCS. It’s really cool, and helpful in many
situations. A popular combination is Git + GitHub.

## <span id="Basic-data-management-5" class="toc-mod-link"></span><span class="toc-item-num">5  </span>Basic data management<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-data-management"
class="anchor-link">¶</a>

-   Save **raw data in a separate directory** (`data/` or `raw_data/`),
    and make it read-only
-   Never duplicate (data) files unless necessary, **use symbolic
    links** instead
-   Keep **large files compressed** (gzip)
-   **Back up crucial files** like raw data files, scripts and
    notes/documentation in at least two spatially distinct locations
    (external drive next to the computer is not good enough in case of
    fire/theft/alien attack/etc.), according to the [3-2-1
    rule](https://en.wikipedia.org/wiki/Backup#:~:text=The%203%2D2%2D1%20rule%20can%20aid%20in%20the%20backup%20process.%20It%20states%20that%20there%20should%20be%20at%20least%203%20copies%20of%20the%20data%2C%20stored%20on%202%20different%20types%20of%20storage%20media%2C%20and%20one%20copy%20should%20be%20kept%20offsite%2C%20in%20a%20remote%20location%20(this%20can%20include%20cloud%20storage).)
    -   For advanced use cases, you can use a backup tool like
        [restic](https://www.reddit.com/r/selfhosted/comments/10v6x3k/help_me_choose_between_borg_restic_and_rclone/)
        or [Borg](https://github.com/borgbackup/borg) that provide
        deduplication, compression and encryption; a file
        synchronization tool like
        [FreeFileSync](https://freefilesync.org/) can also be useful
-   **Make data analysis-friendly**:
    -   Convert to open, non-proprietary, standardized formats that can
        be easily re-used later
    -   Modify cryptic variable names and file names to make them more
        informative
    -   [Tidy up the data](http://garrettgman.github.io/tidying/)
-   **Directory names**:
    -   *chronological*: name is a date, e.g. `2018-03-15` (YYYY-MM-DD
        naming scheme for better sorting); useful if you have many
        experiments of the same type differing by date
    -   *logical*: name is an abstraction of the content, e.g.
        `assembly_first`
    -   *semi-logical* (often best option): name starts with number or
        date → sequence of steps (e.g. `01_filter`, `02_parse`,
        `03_visualization`, etc.)
-   **Name files to reflect their function or content** in chronological
    order, e.g. a file name like
    `dna_sample1.trimmed.filtered.assembled.filtered.fasta` tells you
    exactly what happened to the data (what did happen to the data?)
-   **Temporary file names** should be distinct from permanent file
    names, so you know which files are incomplete or irrelevant
    -   You can rename files in a separate step; e.g. while writing to a
        file, give it a temporary file name like
        `result_file_1.txt.tmp`, and rename it in a separate line:
        `mv result_file_1.txt.tmp result_file_1.txt`
-   **Delete unnecessary files**, especially if they can be easily
    recalculated (time/storage tradeoff) – keep your workspace clean
    -   E.g. intermediate/temporary files, or experimental files after
        trying something out
    -   Do it as soon as possible, will be harder later on
-   **Archive inactive projects** in a separate archive directory,
    packed as `.tar.gz`
-   **Share your data** using [scientific online
    repositories](https://journals.plos.org/plosone/s/recommended-repositories)
    according to the [FAIR
    principles](https://www.nature.com/articles/sdata201618)

A developer's perfect date

## <span id="Basic-project-management-6" class="toc-mod-link"></span><span class="toc-item-num">6  </span>Basic project management<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-project-management"
class="anchor-link">¶</a>

Having an interesting idea and working on it until you get great results
often leads to frustration rather than success. (Maybe this is why ~90%
of New Year's resolutions
[fail](https://en.wikipedia.org/wiki/New_Year%27s_resolution#Success_rate).)
Instead, you should view every undertaking as a **project** and allocate
additional time for **project management**.

1.  Start out with **project planning**. Define **project
    goals/objectives** (direction you're attempting to move in, and
    specific and measurable outcomes)
    -   This defines the **project scope**, the body of work required to
        successfully accomplish the project; the scope determines the
        boundaries of the project, and tells what is *in scope*
        (necessary for project success) and *out of scope* (waste of
        time, at least for project success)
2.  Outline the **milestones** necessary to reach the objectives – each
    milestone should correspond to results (**deliverables**), tangible
    things created from your work, that can be presented as a short
    progress report
    -   Draft a **project schedule** using e.g. a [Gantt
        chart](https://en.wikipedia.org/wiki/Gantt_chart) or a [network
        diagram](https://en.wikipedia.org/wiki/Program_evaluation_and_review_technique#Next_step,_creating_network_diagram_by_hand_or_by_using_diagram_software)
    -   The current project status should always be transparent to you,
        your [PI](https://en.wikipedia.org/wiki/Principal_investigator)
        and your collaborators.
3.  Outline the **work packages** (specific steps) required to reach
    each milestone
4.  Assess the **time and resources** required to complete each work
    package
    -   Each work package should be disassembled into **single steps**,
        **as fine-grained as possible**; you can create a `TODO` file
    -   Think about possible difficulties **in advance** and how you can
        overcome them ([risk
        analysis](https://en.wikipedia.org/wiki/Risk_assessment#Project_management);
        trivial example: if the project is to read a book, and there is
        a risk that it's too dark to read, you can plan for getting a
        lamp or reading during the day)
5.  **Reserve time for work packages in a (online) calendar in advance**
    ([timeblocking](https://en.wikipedia.org/wiki/Timeblocking))
    -   Prioritize according to the [Eisenhower
        method](https://en.wikipedia.org/wiki/Time_management#The_Eisenhower_Method)
        ([example](https://shekhargulati.com/2019/09/01/mental-models-for-software-engineers-improve-your-productivity-by-using-the-eisenhower-matrix/))
    -   Plan the day before (in the evening)
6.  **Use the reserved time** to complete the work packages
    -   Some people like the [Pomodoro
        technique](https://en.wikipedia.org/wiki/Pomodoro_Technique),
        but not everybody
7.  Regularly re-evaluate the project progression, and adapt the
    planning if required. If the anticipated cost-to-benefit ratio of
    the project drops below zero longer-term, abandon the project.

## <span id="Collaborating-on-computational-projects-7" class="toc-mod-link"></span><span class="toc-item-num">7  </span>Collaborating on computational projects<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Collaborating-on-computational-projects"
class="anchor-link">¶</a>

-   Communication is key; create a framework for **talking regularly**
    and discussing experimental and computational progress. (When people
    just send over data or problem descriptions and wait for the
    solution – most likely it will be inadequate)
-   Design experiments and analyses together and prepare for multiple
    iterations
-   Use a VCS like Git to manage changes to a project, and make the
    repository accessible for your collaborators
-   Keep changes small (= group of edits that you might want to undo in
    one step), share changes frequently (synchronize your progress with
    the progress of others), use an additional checklist (log file) for
    keeping track of and sharing changes to the project
-   Daily backup: Store each project in a folder that is **daily
    mirrored** to Dropbox or a remote repository like GitHub (and/or use
    some automated daily backup system)

### <span id="Basic-manuscript-management-7.1" class="toc-mod-link"></span><span class="toc-item-num">7.1  </span>Basic manuscript management<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Basic-manuscript-management"
class="anchor-link">¶</a>

-   Agree with all authors on the workflow before the writing starts
-   Keep a **single master document online** which allows to track
    changes and is available to all co-authors, using a platform like
    Google Docs
-   Alternatively, keep the manuscript in plain text format under
    version control, using **LaTeX** or **Markdown**
-   Keep supplementary materials in separate text-format files for
    easier re-use by others

## <span id="Cyber-security:-passwords-and-encryption-8" class="toc-mod-link"></span><span class="toc-item-num">8  </span>Cyber security: passwords and encryption<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Cyber-security:-passwords-and-encryption"
class="anchor-link">¶</a>

-   For a secure password, use a personalized
    [passphrase](https://www.useapassphrase.com/) (to decrypt something
    locally, like your hard drive or your password manager) and a
    **password manager** like
    [Bitwarden](https://www.reddit.com/r/Bitwarden/comments/tooctc/welcome_to_rbitwarden/),
    [Proton Pass](https://www.reddit.com/r/ProtonPass/) or
    [KeePassXC](https://keepassxc.org/docs/KeePassXC_GettingStarted.html)
    (for logging in to websites and other servers)
    -   Let the password manager generate secure passwords for you
    -   Both approaches are much more secure than the frequent practice
        of taking a word and replacing characters by numbers and special
        characters
        ([security.stackexchange.com](https://security.stackexchange.com/questions/6095/xkcd-936-short-complex-password-or-long-dictionary-passphrase/6096#6096),
        [webroot.com](https://web.archive.org/web/20241102175757/https://www.webroot.com/blog/2019/02/07/the-reality-of-passphrase-token-attacks/))
    -   Ideally, don't re-use the same password on any two sites
    -   Don't change your passwords without need; instead, use a service
        like
        [haveibeenpwned.com](https://bitwarden.com/blog/have-you-been-pwned/)
        to check if accounts were compromised
    -   The best practices to **backup the Bitwarden vault** are
        described
        [here](https://www.reddit.com/r/Bitwarden/comments/o8u50r/comment/h37i5z7/?utm_source=share&utm_medium=web2x&context=3)
-   For accounts that require the highest level of security
    ([reddit](https://www.reddit.com/r/LifeProTips/comments/mapnmv/lpt_set_up_two_factor_authentication_for/)),
    use **two-factor authentication** (2FA, also called multi-factor
    authentication,
    [MFA](https://en.wikipedia.org/wiki/Multi-factor_authentication))
    and an authenticator like the open-source [Proton
    authenticator](https://proton.me/authenticator) or [Ente
    Auth](https://github.com/ente-io/ente)
    -   Consider using 2FA at least for your password manager and your
        main email account
        ([reddit](https://www.reddit.com/r/Bitwarden/comments/qt6igt/what_should_i_know_before_i_start_using_bitwarden/))
    -   Make sure to **save the 2FA recovery codes** in a safe place,
        e.g. a second password manager account, otherwise you risk
        losing access to your account
        ([reddit](https://www.reddit.com/r/Bitwarden/comments/kqkeau/where_do_you_store_your_2fa_backup_codes/))
    -   [Many
        services](https://blog.google/inside-google/googlers/ask-a-techspert/how-passkeys-work/)
        are changing their preferred authentication method from
        passwords to **passkeys**
        ([YouTube](https://www.youtube.com/watch?v=bdp8RdjV6PU),
        [passkeys.com](https://www.passkeys.com/what-are-passkeys),
        [bitwarden.com](https://bitwarden.com/resources/passkeys-faq/)),
        which are generally more secure and more convenient
        ([YouTube](https://www.youtube.com/watch?v=EA9mK3nJE1o),
        [reddit](https://www.reddit.com/r/privacy/comments/1eiin9x/can_someone_please_explain_passkeys/),
        [reddit](https://www.reddit.com/r/Bitwarden/comments/17m4hv4/can_someone_explain_passkeys_to_me_and_why_i/)),
        but not without caveats
        ([YouTube](https://www.youtube.com/watch?v=_tQbWop1P7o))
-   For sensitive data on your computer, use full disk encryption, which
    is often the default setting on modern operating systems
    ([reddit](https://www.reddit.com/r/archlinux/comments/1aihaep/how_important_is_disk_encryption/))
-   For sensitive data that you want to store offline, use an encryption
    tool like
    [VeraCrypt](https://www.howtogeek.com/108501/the-how-to-geek-guide-to-getting-started-with-truecrypt/)
    or
    [Cryptomator](https://docs.cryptomator.org/en/latest/desktop/getting-started/)
-   For sensitive data that you want to store in a cloud drive, use a
    tool like
    [Cryptomator](https://docs.cryptomator.org/en/latest/desktop/getting-started/)
    or [rclone](https://rclone.org/)
-   For sensitive communication, use tools providing end-to-end
    encryption
    -   Open-source tools are usually preferable, because their source
        code can be inspected and double-checked by others
    -   You should be aware that many traditional communication services
        likes emails are inherently insecure
        ([stackexchange.com](https://security.stackexchange.com/questions/30087/good-simple-list-of-reasons-that-email-is-inherently-insecure/))
-   If possible, use SSH with **public/private keys** ([public-key
    cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography))
    instead of password authentication
    ([reddit](https://www.reddit.com/r/linuxquestions/comments/ehapud/ssh_keys_vs_password/),
    [dev.to](https://dev.to/risafj/ssh-key-authentication-for-absolute-beginners-in-plain-english-2m3f),
    [digitalocean.com](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server),
    details:
    [digitalocean.com](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys))
    -   It's much nicer to use SSH for [GitHub
        authentication](https://docs.github.com/en/authentication/connecting-to-github-with-ssh),
        as you won't need to enter your credentials anymore (you can
        also use [Git Credential
        Manager](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git#git-credential-manager))
    -   You can also use SSH to log in to your VM guest, from the host
        or another machine
        ([makeuseof.com](https://www.makeuseof.com/how-to-ssh-into-virtualbox-ubuntu/))
    -   On Windows, [MobaXterm](https://mobaxterm.mobatek.net/) is a
        popular tool for SSH connections, it's more versatile than PuTTY
    -   If you want to SSH into your local network (e.g. your computer
        or VM at home) from anywhere, use
        [Wireguard](https://ubuntu.com/server/docs/wireguard-vpn-introduction)
        to create a VPN tunnel

## <span id="Beware-of-...-9" class="toc-mod-link"></span><span class="toc-item-num">9  </span>Beware of ...<a
href="https://moodle.fhwn.ac.at/pluginfile.php/930919/mod_resource/content/0/Best-practices-cheatsheet.html#Beware-of-..."
class="anchor-link">¶</a>

-   **Manual modification** of output files
    -   Workflow becomes non-reproducible
    -   You WILL forget later what you did
-   **Messy workspace**
    -   with lots of different files lying around, taking up space and
        making you nervous (sounds funny, but this is what actually
        happens)
-   **Poorly tested/unjustified analysis steps**
    -   Using non-default parameters, unpublished tools or untested
        workflows without very good reason → this will be much, much
        harder to publish
-   **“Overfitting”**
    -   Fine-tuning the workflow (e.g. tool parameters) to achieve the
        "desired" results
    -   The results may become slightly better, but less reproducible
        and harder to publish
-   **Confirmation bias** (human tendency to handle information in a way
    that confirms one’s preexisting beliefs or hypotheses)
    -   Don’t "adapt" the analysis to your ideas about what the results
        should be; this might give seemingly better results short-term,
        but will cause more problems long-term
    -   This is not the same as optimizing the workflow by identifying
        the tools/approaches best-suited for your data to obtain good
        results :)
    -   Rule of thumb: A good result is often stable towards changes in
        parameters and even analysis methods. If it is not, it might not
        be a reliable result.
