# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!--

============== Guiding Principles ==============

* Changelogs are for humans, not machines.
* There should be an entry for every single version.
* The same types of changes should be grouped.
* Versions and sections should be linkable.
* The latest version comes first.
* The release date of each version is displayed.
* Mention whether you follow Semantic Versioning.

============== Types of changes (keep the order) ==============

* `Added` for new features.
* `Changed` for changes in existing functionality.
* `Deprecated` for soon-to-be removed features.
* `Removed` for now removed features.
* `Fixed` for any bug fixes.
* `Security` in case of vulnerabilities.
* `Dependencies Update` in case of vulnerabilities.
* `Contributors` to thank the contributors that worked on this PR.

============== How To Update The Changelog for a New Release ==============

** Always Keep The Unreleased On Top **

To release a new version, please update the changelog as followed:
1. Rename the `Unreleased` Section to the Section Number
2. Recreate an `Unreleased` Section on top
3. Update the links at the very bottom

======================= START: TEMPLATE TO KEEP IN CASE OF NEED ===================

** DO NOT MODIFY THIS SECTION ! **

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

### Security

### Dependencies Update

### Contributors

** DO NOT MODIFY THIS SECTION ! **

======================= END: TEMPLATE TO KEEP IN CASE OF NEED ===================

-->

<!-- YOU CAN EDIT FROM HERE -->

## [Unreleased]

### Added
- API:
  - `tl.model.vgg19` added (PR #698)
  - `tl.logging.contrib.hyperdash` added (PR #739)
  - `tl.distributed.trainer` added (PR #700)
- Documentation:
  - Add binary, ternary and dorefa links (PR #711)
  - Update input scale of VGG16 and VGG19 to 0~1 (PR #736)
- Layer:
  - Release SwitchNormLayer (PR #737)
- Setup:
  - Creation of installation flaggs `all_dev`, `all_cpu_dev`, and `all_gpu_dev` (PR #739)
- Tutorials:
  - `tutorial_models_vgg19` has been introduced to show how to use `tl.model.vgg19` (PR #698).
  - fix bug of `tutorial_bipedalwalker_a3c_continuous_action.py` (PR #734, Issue #732)
  - `tutorial_models_vgg16` and `tutorial_models_vgg19` has been changed the input scale from [0,255] to [0,1](PR #710)
  - `tutorial_mnist_distributed_trainer.py` and `tutorial_cifar10_distributed_trainer.py` are added to explain the uses of Distributed Trainer (PR #700)

### Changed
  - all the input scale in both vgg16 and vgg19 has been changed the input scale from [0,255] to [0,1](PR #710)
  - Dockerfiles merged and refactored into one file (PR #747)
  - LazyImports move to the most **top level** imports as possible (PR #739)

### Deprecated
  - `tl.logging.warn` has been deprecated in favor of `tl.logging.warning` (PR #739)

### Removed
  - `conv_layers()`  has been removed in both vgg16 and vgg19(PR #710)

### Fixed
- import error caused by matplotlib on OSX (PR #705)
- missing import in tl.prepro (PR #712)
- Dockerfiles import error fixed - issue #733 (PR #747)

### Security

### Dependencies Update
- tensorflow>=1.8,<1.9 => tensorflow>=1.9,<1.10 (PR #739)
- tensorflow-gpu>=1.8,<1.9 => tensorflow-gpu>=1.9,<1.10 (PR #739)
- pymongo>=3.6,<3.7 => tensorflow-gpu>=3.7,<3.8 (PR #750)


### Contributors
- @DEKHTIARJonathan: #739 #747 #750
- @lgarithm: #705 #700
- @OwenLiuzZ: #698 #710
- @zsdonghao: #711 #712 #734 #736 #737 #700
- @luomai: #700

## [1.9.0] - 2018-06-16

### Added
- API:
  - `tl.alphas` and `tl.alphas_like` added following the tf.ones/zeros and tf.zeros_like/ones_like (PR #580)
  - `tl.lazy_imports.LazyImport` to import heavy libraries only when necessary (PR #667)
  - `tl.act.leaky_relu6` and `tl.layers.PRelu6Layer` have been deprecated (PR #686)
  - `tl.act.leaky_twice_relu6` and `tl.layers.PTRelu6Layer` have been deprecated (PR #686)
- CI Tool:
  - [Stale Probot](https://github.com/probot/stale) added to clean stale issues (PR #573)
  - [Changelog Probot](https://github.com/mikz/probot-changelog) Configuration added (PR #637)
  - Travis Builds now handling a matrix of TF Version from TF==1.6.0 to TF==1.8.0 (PR #644)
  - CircleCI added to build and upload Docker Containers for each PR merged and tag release (PR #648)
- Decorator:
  - `tl.decorators` API created including `deprecated_alias` and `private_method` (PR #660)
  - `tl.decorators` API enriched with `protected_method` (PR #675)
  - `tl.decorators` API enriched with `deprecated` directly raising warning and modifying documentation (PR #691)
- Docker:
  - Containers for each release and for each PR merged on master built (PR #648)
  - Containers built in the following configurations (PR #648):
    - py2 + cpu
    - py2 + gpu
    - py3 + cpu
    - py3 + gpu
- Documentation:
  - Clean README.md (PR #677)
  - Release semantic version added on index page (PR #633)
  - Optimizers page added (PR #636)
  - `AMSGrad` added on Optimizers page added (PR #636)
- Layer:
  - ElementwiseLambdaLayer added to use custom function to connect multiple layer inputs (PR #579)
  - AtrousDeConv2dLayer added (PR #662)
  - Fix bugs of using `tf.layers` in CNN (PR #686)
- Optimizer:
  - AMSGrad Optimizer added based on `On the Convergence of Adam and Beyond (ICLR 2018)` (PR #636)
- Setup:
  - Creation of installation flaggs `all`, `all_cpu`, and `all_gpu` (PR #660)
- Test:
  - `test_utils_predict.py` added to reproduce and fix issue #288 (PR #566)
  - `Layer_DeformableConvolution_Test` added to reproduce issue #572 with deformable convolution (PR #573)
  - `Array_Op_Alphas_Test` and `Array_Op_Alphas_Like_Test` added to test `tensorlayer/array_ops.py` file (PR #580)
  - `test_optimizer_amsgrad.py` added to test `AMSGrad` optimizer (PR #636)
  - `test_logging.py` added to insure robustness of the logging API (PR #645)
  - `test_decorators.py` added (PR #660)
  - `test_activations.py` added (PR #686)
- Tutorials:
  - `tutorial_tfslim` has been introduced to show how to use `SlimNetsLayer` (PR #560).
  - add the following to all tutorials (PR #697):
    ```python
    tf.logging.set_verbosity(tf.logging.DEBUG)
    tl.logging.set_verbosity(tl.logging.DEBUG)
    ```

### Changed
- Tensorflow CPU & GPU dependencies moved to separated requirement files in order to allow PyUP.io to parse them (PR #573)
- The document of LambdaLayer for linking it with ElementwiseLambdaLayer (PR #587)
- RTD links point to stable documentation instead of latest used for development (PR #633)
- TF Version older than 1.6.0 are officially unsupported and raises an exception (PR #644)
- README.md Badges Updated with Support Python and Tensorflow Versions (PR #644)
- TL logging API has been consistent with TF logging API and thread-safe (PR #645)
- Relative Imports changed for absolute imports (PR #657)
- `tl.files` refactored into a directory with numerous files (PR #657)
- `tl.files.voc_dataset` fixed because of original Pascal VOC website was down (PR #657)
- extra requirements hidden inside the library added in the project requirements (PR #657)
- requirements files refactored in `requirements/` directory (PR #657)
- README.md and other markdown files have been refactored and cleaned. (PR #639)
- Ternary Convolution Layer added in unittest (PR #658)
- Convolution Layers unittests have been cleaned & refactored (PR #658)
- All the tests are now using a DEBUG level verbosity when run individualy (PR #660)
- `tf.identity` as activation is **ignored**, thus reducing the size of the graph by removing useless operation (PR #667)
- argument dictionaries are now checked and saved within the `Layer` Base Class (PR #667)
- `Layer` Base Class now presenting methods to update faultlessly `all_layers`, `all_params`, and `all_drop` (PR #675)
- Input Layers have been removed from `tl.layers.core` and added to `tl.layers.inputs` (PR #675)
- Input Layers are now considered as true layers in the graph (they represent a placeholder), unittests have been updated (PR #675)
- Layer API is simplified, with automatic feeding `prev_layer` into `self.inputs` (PR #675)
- Complete Documentation Refactoring and Reorganization (namely Layer APIs) (PR #691)

### Deprecated
- `tl.layers.TimeDistributedLayer` argurment `args` is deprecated in favor of `layer_args` (PR #667)
- `tl.act.leaky_relu` have been deprecated in favor of `tf.nn.leaky_relu` (PR #686)

### Removed
- `assert()` calls remove and replaced by `raise AssertionError()` (PR #667)
- `tl.identity` is removed, not used anymore and deprecated for a long time (PR #667)
- All Code specific to `TF.__version__ < "1.6"` have been removed (PR #675)

### Fixed
- Issue #498 - Deprecation Warning Fix in `tl.layers.RNNLayer` with `inspect` (PR #574)
- Issue #498 - Deprecation Warning Fix in `tl.files` with truth value of an empty array is ambiguous (PR #575)
- Issue #565 related to `tl.utils.predict` fixed - `np.hstack` problem in which the results for multiple batches are stacked along `axis=1` (PR #566)
- Issue #572 with `tl.layers.DeformableConv2d` fixed (PR #573)
- Issue #664 with `tl.layers.ConvLSTMLayer` fixed (PR #676)
- Typo of the document of ElementwiseLambdaLayer (PR #588)
- Error in `tl.layers.TernaryConv2d` fixed - self.inputs not defined (PR #658)
- Deprecation warning fixed in `tl.layers.binary._compute_threshold()` (PR #658)
- All references to `tf.logging` replaced by `tl.logging` (PR #661)
- Duplicated code removed when bias was used (PR #667)
- `tensorlayer.third_party.roi_pooling.roi_pooling.roi_pooling_ops` is now lazy loaded to prevent systematic error raised (PR #675)
- Documentation not build in RTD due to old version of theme in docs directory fixed (PR #703)
- Tutorial:
  - `tutorial_word2vec_basic.py` saving issue #476 fixed (PR #635)
  - All tutorials tested and errors have been fixed (PR #635)

### Dependencies Update
- Update pytest from 3.5.1 to 3.6.0 (PR #647)
- Update progressbar2 from 3.37.1 to 3.38.0 (PR #651)
- Update scikit-image from 0.13.1 to 0.14.0 (PR #656)
- Update keras from 2.1.6 to 2.2.0 (PR #684)
- Update requests from 2.18.4 to 2.19.0 (PR #695)

### Contributors
- @lgarithm: #563
- @DEKHTIARJonathan: #573 #574 #575 #580 #633 #635 #636 #639 #644 #645 #648 #657 #667 #658 #659 #660 #661 #666 #667 #672 #675 #683 #686 #687 #690 #691 #692 #703
- @2wins: #560 #566 #662
- @One-sixth: #579
- @zsdonghao: #587 #588 #639 #685 #697
- @luomai: #639 #677
- @dengyueyun666: #676

## [1.8.5] - 2018-05-09

### Added
- Github Templates added (by @DEKHTIARJonathan)
  - New issues Template
  - New PR Template
- Travis Deploy Automation on new Tag (by @DEKHTIARJonathan)
  - Deploy to PyPI and create a new version.
  - Deploy to Github Releases and upload the wheel files
- PyUP.io has been added to ensure we are compatible with the latest libraries (by @DEKHTIARJonathan)
- `deconv2d` now handling dilation_rate (by @zsdonghao)
- Documentation unittest added (by @DEKHTIARJonathan)
- `test_layers_core` has been added to ensure that `LayersConfig` is abstract.

### Changed
- All Tests Refactored - Now using unittests and runned with PyTest (by @DEKHTIARJonathan)
- Documentation updated (by @zsdonghao)
- Package Setup Refactored (by @DEKHTIARJonathan)
- Dataset Downlaod now using library progressbar2 (by @DEKHTIARJonathan)
- `deconv2d` function transformed into Class (by @zsdonghao)
- `conv1d` function transformed into Class (by @zsdonghao)
- super resolution functions transformed into Class (by @zsdonghao)
- YAPF coding style improved and enforced (by @DEKHTIARJonathan)

### Fixed
- Backward Compatibility Restored with deprecation warnings (by @DEKHTIARJonathan)
- Tensorflow Deprecation Fix (Issue #498):
  - AverageEmbeddingInputlayer (by @zsdonghao)
  - load_mpii_pose_dataset (by @zsdonghao)
- maxPool2D initializer issue #551 (by @zsdonghao)
- `LayersConfig` class has been enforced as abstract
- Pooling Layer Issue #557 fixed (by @zsdonghao)

### Dependencies Update
- scipy>=1.0,<1.1 => scipy>=1.1,<1.2

### Contributors
@zsdonghao @luomai @DEKHTIARJonathan

[Unreleased]: https://github.com/tensorlayer/tensorlayer/compare/1.9.0...master
[1.9.0]: https://github.com/tensorlayer/tensorlayer/compare/1.9.0...1.8.5
[1.8.5]: https://github.com/tensorlayer/tensorlayer/compare/1.8.4...1.8.5
