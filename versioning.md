# Create new article version

If an article has been published (scheduled for publication) a new article version can be created at the production stage of the submission. Old versions are displayed in a tab view and can not be edited again.

A click on the button _new version_ creates a new unpublished version of the article. The new version is displayed at a new tab and contains all metadata of the previous version except the publication date. The new version can be edited and published when ready.

![versioning_tab_unpublished](https://raw.githubusercontent.com/lilients/img/master/versioning_tab_unpublished.png)

To prevent errors the button new version is only displayed if the recent version has been published.

![versioning](https://raw.githubusercontent.com/lilients/img/master/versioning_tab.png )

The metadata view at the top of the page will always display the metadata of the most recent article version. The metadata of each version can be viewed at the version tab. "Schedule for publication" is also displayed for each version.

The conversation at the bottom of the page is not bound to a specific version. As well as the production ready files.

## Versioned metadata
The following metadata can be changed at a new version: prefix, title, subtitle, abstract, contributors, date_published, licence. DOIs are generated with a version number.

Extended submission metadata will not be considered (e.g. keywords, subject, language, etc.). Also the cover image is currently only stored for the article and not for each version.

## Uploading a new file version

Published files are attached to galleys. Each galley has only one file. The user can change the galley file attached to the galley by using the function _change file_. 

![versioning](https://raw.githubusercontent.com/lilients/img/master/versioning_change-file.png)

# Display of versions at the frontend

Only the current version of the article is linked at the table of contents of the issue. Old versions of the article are displayed at the article page. [Example](http://ojs-test.cedis.fu-berlin.de/ojsde-versioning/index.php/test/article/version/3/1)

![versioning](https://raw.githubusercontent.com/lilients/img/master/versioning_frontend-latest.png)

Each article version is being displayed at an article page with the corresponding metadata of the version. 
Old versions have an indication and link to the current version of the article.

![versioning](https://raw.githubusercontent.com/lilients/img/master/versioning_frontend-old.png)

## Citation formats

The metadata of the displayed version is also displayed at the "How to Cite" block.

![citation](https://raw.githubusercontent.com/lilients/img/master/versioning_howToCite1.png)

If there is a URL in the citation stile, it will always display the URL with version number or the doi of this version. This way the correct version will be cited.

## URL structure

The URL structure of the current article is unchanged (backward compatability) but there is a link with the version number as well. Old versions can only be accessed via the version URL.

* current article version: .../article/view/[articleId]
* old article version: .../article/version/[articleId]/[version]
* current galley version: .../article/view/[articleId]/[galleyId]
* old galley version: .../article/version/[articleId]/[version]/[galleyId]

## Google Scholar 

As each version is displayed at its own article page, the metadata for GoogleScholar (in dublin core) displays also the metadata of this version.
