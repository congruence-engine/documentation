# Congruence Engine, Layout Parser Notes**
* Layout parser describes itself as a ‘toolkit’. Its ‘Deep Layout Parsing’ feature, which we’re most interested in, is really just a wrapper around Facebook’s Detectron2 platform, with a model zoo containing a handful of object detection models trained on some available layout datasets (see below). 
* For customisation purposes there’s a data annotation web service which can be quickly spun up, but this also is essentially a wrapper around Layout Studio alongside a (very homespun) model server which returns a starting set of annotations. This service then stores the annotations which can then be downloaded as a training set.
* There is a separate repo with some (also homespun) scripts for training 
* I haven’t (yet) found anything on efficient retraining of LP type models, and the existing models are very much ‘all or nothing’.
* … that said, there looks to be some research into few-shot learning which might be effective? (See below)
* … or it’s just worth spending some more time with the Prima and NewspaperLayout models to see if they might yield adequate results.
* The annotation service GitHub repo hints at an ‘active learning’ backend, but this isn’t implemented and there would appear to be no roadmap for doing so.
* I’ve spun up an example of the annotation service here: [Label Studio](~http://138.68.174.67:8080~)
* Has an active Slack community, w/ 472+ members and looks fairly responsive to qus.

### Datasets for Prima and Newspaper Layout…
* Prima has a variety of document types, magazine scans and technical articles in particular: [PRImA Contemporary Dataset](~https://www.primaresearch.org/dataset/~)
* Newspaper Navigator comes from the WW1-era Chronicling America collection at the LoC: [Newspaper Navigator  |  Experiments  |  Work  |  Library            of Congress](~https://news-navigator.labs.loc.gov~)

### Few-shot Learning
Few-shot tweaking of an existing Detectron2-type model might be a thing, see e.g. https://arxiv.org/pdf/2203.12224.pdf

### Detectron2
Detectron2 is described as a “research platform for object detection”. Supports a bunch of different object detection models, including e.g. [Mask R-CNN](~https://viso.ai/deep-learning/mask-r-cnn/~) which looks to be one of the models used to train the ‘deep layout parser’. As a side note I wonder about the suitability of this, and whether other models wouldn’t be much more effective.. an ensemble network which incorporates specific OCR capabilities maybe?