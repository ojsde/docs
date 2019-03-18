# Technical documentation of article publishing

Versioning for published articles has been developed at the ojs-de.net project in Berlin.

New versions can be created of published articles. Newly created versions get a copy of the metadata (without publication date) and galleys of the recent version.

See GUI description: https://github.com/lilients/ojs/wiki/Article-versioning-in-OJS

## URL structure

The URL structure of the current article remains the same. You can always get the latest version of an article and its galleys at this URL:

* current article version: .../article/view/[articleId]
* current galley version: .../article/view/[articleId]/[galleyId]

Additionally the latest version does also have an URL containing the version number (this is useful to cite this specific version). Older versions of an article can only be accessed via the version URL:

* specific article version: .../article/version/[articleId]/[version]
* specific galley version: .../article/version/[articleId]/[version]/[galleyId]

If you use custom identifier instead of the genereated article ids, the URL structure is the same as described above, only with the custiom identifier at the place of the article id.

## DOIs and versioning
If DOIs are enabled for the journal, the default setting will be expanded per default by the version number. This means that the version number is always added to DOI, even if there is only one version.

* DOIs at article level are stored in <code>submission_settings</code>
* DOIs at galley level are stored in <code>submission_galley_settings</code>

## Database structure

### Metadata
The metadata of a submission is stored in the following tables:

* <code>submissions</code> stores information about the submission (e.g. stage_id, date_submitted, etc.)
* <code>published_submissions</code> stores the metadata of a published submission (<code>date_published</code> has been moved from here to <code>submission_settings</code>, to allow article versions with different publication dates)
* <code>submission_settings</code> stores the metadata that can differ between article versions (and translations)

| submission_id | submission_version | locale | setting_name | setting_value | setting_type |
| ------------- | ------------------ | ------ | ------------ | ------------- | ------------ |
| 7 | 1 | | datePublished | 2017-05-01 | string |
| 7 | 1| ...| ...| ...| ...|
| 7| 2| | datePublished| 2017-05-08| string|
| 7| 2| ...| ...| ...| ...|

### Authors
A collumn for the version number has been added to the <code>author_settings</code> table:

| author_id | submission_version | locale | setting_name | setting_value |  setting_type |
| --------- | ------------------ | ------ | ------------ | ------------- | ------------- |
| 4 | 1 | de_DE | lastName | Schmidt | string |
| 4 | 2 | de_DE | lastName | Müller | string |

### Galleys
Similar to the metadata of a submission, the galley's metadata needs to be versionized. The same structure has been added to the corresponding tables (the files have been moved to a new table <code>submission_galley_files</code>, so the galley settings can be stored for each version).

* <code>submission_galley</code> stores the metadata at galley level
* <code>submission_galley_settings</code> stores the metadata that is relevant for versions (and translations)
* <code>submission_galley_files</code> stores the galley files for each submission revision

## Interfaces

### Google Scholar

As each version is displayed at its own article page, the metadata for GoogleScholar (in dublin core) displays also the metadata of this version.

### OAI
Only the metadata of the recent article is displayed at the OAI interface.
