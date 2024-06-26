# Checklist

A personal checklist, according to concepts of SE, to go through in such implementations (A scientific demo in the quantum software field)

- [ ] Identify the domain and problem
    - [ ] Write down the problem at hand in natural language
    - [ ] Create mind map of the problem and it's related matters
- [ ] Create SRS document for project with the following sections (complete and refine document as the project goes on)
    - [ ] The purpose of this document
    - [ ] Scope and our of scope
    - [ ] Intent audience
    - [ ] Use cases and usage instructions
    - [ ] Dictionary
    - [ ] Functional requirements
    - [ ] Non-functional requirements
    - [ ] Hardware requirements
    - [ ] Installation / Running the project
- [ ] Create list of key phrases
- [ ] Get the *base* information and knowledge about the key phrases and concepts
- [ ] Identify the best-suited tools for the problem
- [ ] Formally express an outline for the solution and approach
- [ ] Formally verify the implementation
- [ ] Gather the required input data for the demonstration(if needed)
    - [ ] Validate the data
- [ ] Implement (*Beware of premature optimization!)
    - [ ] Implement the most basic and simplified case
    - [ ] Incrementally add the rest
    - [ ] Make the environment as deterministic as possible -> Add strict linting, add version checking for your env, strict dotfiles(.python-version , .nvmrc, .gitattributes, .editorconfig)
    to make sure the code and it's execution is as reproducible and homogeneous as possible
- [ ] Refine or re-iterate implementation if needed
- [ ] Optimize
- [ ] Write execution tests to be sure the demo can be accessed and ran in the future, and to have indicators to know when the project is outdated and irrelevant
- [ ] Make sure every part of the code and the thought process is clear and understandable and correct
- [ ] Make sure every related resource to the project (code, tests, docs, license, papers, etc. ) are put together in an accessible and safe place

## Notes
- Make sure to keep track of the references that the project is moving based off of and cite them(have organized bibliography)
- Beware of premature optimization. First make sure the project is on the right track, the thought process is correct, and get some working versions before starting to optimize
- Make sure the project (at least the docs) are peer-reviewed, by people on the spectrum(from most competent to least competent) of your intent audience, and make sure it is understandable by all of them
