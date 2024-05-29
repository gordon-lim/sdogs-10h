# SDOGS-10H

SDOGS-10H consists of 7,500 time-limited human annotations over 250 dog images sourced from the [Stanford Dogs dataset](http://vision.stanford.edu/aditya86/ImageNetDogs/). Thirty participants were randomly assigned to one of three cohorts, with ten participants in each cohort, and viewed the images for durations of 100ms, 1000ms, or 2500ms, respectively. Additionally, we include our participants’ responses from the post-study survey, including psychometric questionnaire scores.

The repository supports our [AAAI HCOMP 2024](https://www.humancomputation.com/) paper submission **"Towards Fair Pay and Equal Work: Imposing View Time Limits in Crowdsourced Image Classification"** and includes the analyses we performed to evaluate view time limits in image classification crowdsourcing tasks as a practical approach to addressing ethical concerns around fair compensation and task completion transparency.

### Repository Contents

`prolific-data.csv` - This file contains data collected from participants during the time-limited test. Each row corresponds to a participant's answer to each image used in the test. The columns are as follows:

* `participant_id` is a unique integer ID for each participant on Prolific, used in place of their actual Prolific ID to preserve anonymity.
* `viewtime` is the duration (ms) participants were given to view the image before they could submit their answer. One of 100, 1000, or 2500ms.
* `test_qid` indexes the dog images in the same order that all participants annotated.
* `timetaken` is the duration (ms) participants spent on the current `test_qid`, recorded from when they pressed 'F' to when they submitted their answer.
* `answer` is the string class name (e.g., "Yorkshire terrier") chosen by the participant for the image.
* `stanford_label` is the given string class label of the image from the Stanford Dogs dataset.
* `stanford_label_idx` is the given class label index of the image from the Stanford Dogs dataset.
* `stanford_sampleid` is the integer ID of the image within the Stanford Dogs dataset.
* `image_name` is the string file name of the Stanford Dogs image.
* `image_filename` is the filename of the JPG file for the stimulus.

`qualtrics-data.csv` - This file contains data collected from participants in our post-study [Qualtrics](https://www.qualtrics.com/) survey. Each row corresponds to an individual participant's responses to our survey questions. The columns are as follows:

* `participant_id` is the same as above.
* `duration` is the time in seconds that participants spent on the survey as recorded by Qualtrics.
* `pet_dog` is the open-ended response to "Do you currently own or have you ever owned a pet dog? If yes, please specify the breed(s)."
* `difficulty` is the open-ended response to "Please comment on the difficulty of the task (e.g., time was too limited)."
* `features` is the open-ended response to "Describe the features of images that you felt you needed more time on."
* `feedback` is an open-ended response to "Any general comments/feedback?"
* `prolific_time` is the multiple-choice response to "How much time, on average, do you spend on Prolific/MTurk each week for various tasks, including participating in studies or completing tasks? Please select the option that best represents your weekly commitment."
* `PosAffect` is the Positive Affect score on the [Positive And Negative Affect Schedule (PANAS)](https://ogg.osu.edu/media/documents/MB%20Stream/PANAS.pdf).
* `NegAffect` is the Negative Affect score on the [Positive And Negative Affect Schedule (PANAS)](https://ogg.osu.edu/media/documents/MB%20Stream/PANAS.pdf).
* `ATTC_FOC` is the attention focusing score on the [Attention Control Scale](https://arc.psych.wisc.edu/self-report/attention-control-scale-attc/).
* `ATTC_SHIF` is the attention shifting score on the [Attention Control Scale](https://arc.psych.wisc.edu/self-report/attention-control-scale-attc/).

`analysis.ipynb` - This Jupyter notebook contains our analysis to create the plots in our paper. We conducted a comparative analysis between data from our time-limited study and prior work, [CIFAR-10H](https://github.com/jcpeterson/cifar-10h), which did not use a time limit. Download `data/cifar10h-raw.csv` from [here](https://github.com/jcpeterson/cifar-10h). The analysis addresses the following six research questions:

* RQ1: Does time pressure affect performance?
* RQ2: Do annotators who spend more time have greater label certainty?
* RQ3: What is the trade-off between data quality and varying time limits?
* RQ4: Which images are more difficult under time limits?
* RQ5: Do declines in accuracy correlate with increased uncertainty?
* RQ6: How does a time limit affect the satisfaction/motivation of crowd workers?

## Erratum: Cat Image

In our study, we mistakenly included a cat image instead of a dog (test_qid 171). This image was then shown as a broken image to participants after it was removed. We excluded all related data from our analysis. This error came from a previous research direction using cat images as attention checks. Since only one image was affected, we believe this error does not impact our conclusions or discredit our contributions. The remaining data accurately supports our findings.

## Acknowledgements

We would like to thank the authors of [CIFAR-10H](https://github.com/jcpeterson/cifar-10h/tree/master) and [DiD](https://github.com/computational-imaging/diffusion-in-the-dark/tree/main), which we referenced in creating this README.

