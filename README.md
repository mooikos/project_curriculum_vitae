# Project Curriculum Vitae

Support creation and maintenance of my Curriculum Vitae with AI.

## positions

```
rails developer
ruby developer
qa engineer
test engineer
```

## generate pdf CV

- ask Gemini to generate the CV
```
brew install --cask antigravity-cli

# start and login to cli
agy

# inquiry
Role: You are an expert technical recruiter and resume writer.
Task: I am providing my master CV in JSON format and a target Job Description. Please tailor my CV to this specific role.
Rules:

Select only the most relevant skills, tools, and bullet points from my JSON that match the Job Description.
Subtly reword my responsibilities to mirror the keywords and language used in the job ad.
PLEASE DO NOT inventing experiences, in case of need ask me questions to expand the master_info with relevant info.
Whenever I confirm extra skills, tools, or responsibilities through your questions, please also update ../master_info.json with those confirmed additions so they are persisted for future applications.
Keep ../master_info.json clean, unified, and concise: merge related competences into short, atomic keywords/phrases and prune redundant or overly wordy sentences.
Always re-read target files (especially ../master_info.json, ../target_job_ad.text, and ./adapted_master_info.tex) right before changing them or generating output, as I may have updated them manually in the meantime.
Keep the output concise (maximum 1-2 pages).
Output the final tailored resume strictly in LaTeX code using the jakegut/resume template structure.

you can find my CV "master file" in: ../master_info.json
you can find the target job role/ad in (I might have updated it to a new one): ../target_job_ad.text
please output the latex text in: ./adapted_master_info.tex

I will run the docker code myself,
please just create the latex file adapted from the other 2

in case you are confused just check the readme for myself in the parent folder
```
- run from the [resume](https://github.com/sb2nov/resume) project folder
```
docker run --rm -i -v "$PWD":/data latex pdflatex adapted_master_info.tex
mv ./adapted_master_info.pdf ./2026_de_vivo_massimiliano_cv.pdf
```
