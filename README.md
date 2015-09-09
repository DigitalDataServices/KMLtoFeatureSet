# KML to FeatureSet

Converts Google Earth KML/KMZ files to one or more ArcGIS FeatureSets (one for each feature type) so that it can be passed as an input argument into other Geocortex workflow activites. This includes a custom DLL and sample workflow for Latitude Geographics Geocortex Workflow Designer.

## Installation

To use a custom workflow module, you will need to copy the "DDS.KmlWorkflow.dll" to the following directories in your Geocortex Essentials installation. If you have a custom installation of Geocortex Essentials, please adjust your file paths appropriately.

- `\Geocortex Essentials\Default\REST Elements\REST\bin`
  - Default path is `C:\Program Files (x86)\Latitude Geographics\Geocortex Essentials\Default\REST Elements\REST\bin\`
  - This location makes the dll available to the REST endpoint and your users.

- `\Geocortex Essentials\Default\Workflow Designer`
  - Default path is `C:\Program Files (x86)\Latitude Geographics\Geocortex Essentials\Default\Workflow Designer\`
  - This location makes the module available in the Geocortex Workflow Designer.

To use the sample workflow, you will need to copy the "KmlWorkflowExample.xaml" to your sites folder (`\Geocortex Essentials\Default\REST Elements\Sites\`). We recommend that you place it in a "Workflow" directory under the specific site you plan to use it in.

The "KML.png" is provided as an optional graphic for the Toolbar Button.


## Sample Workflow

After installing the "DDS.KmlWorkflow.dll" in the appropriate locations described above, the following steps show how to add a the KML Import Workflow to a Geocortex Site with an HTML5 Viewer as a Toolbar Button

- Start your Geocortex Essentials Manager and open the Site that you will be adding the KML workflow to.
- Select the "Workflows" from the Site Table of Contents.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/01-workflow-site-tab.png)

- Add a new Workflow and name it accordingly (e.g. "KmlImportWorkflow").
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/02-add-workflow.png)
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/03-add-workflow-wizard.png)

- For the URI, choose "Browse..." and select the "KmlWorkflowExample.xaml" file that was copied to your Sites directory earlier. Click "Next" and then "Finish.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/04-browse-workflow-location.png)

- Save the modified Site.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/05-save-site.png)

- Next, attach the KmlImportWorkflow to a Viewer Toolbar Button. Select the "Viewers" Site Tab
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/06-add-to-viewer.png)

- "Edit" the Viewer that will contain the KML Import Button.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/07-edit-viewer.png)

- Select the "Toolbar" Viewer Tab under the "Viewer for HTML5 ..." Header.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/08-site-toolbar.png)

- Next add a new "Tab" to the Toolbar (optionally, you can add a new Button to an existing Tab).
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/09-add-tab1.png)
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/10-add-tab2.png)

- Add a new "Group" to the Tab.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/11-edit-group.png)

- Add a new "Button" to the Group.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/12-edit-button.png)

- The "Name" and "Tooltip" fields are user-defined.
- The "Image Uri" field should point to an icon image for the Button (e.g. the "KML.png" file that is provided in the Github repository). You may need to "Upload" the image to your '\Sites\...\VirtualDirectory' or other public location if the image does not exist.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/13-select-file.png)

- The "Command" field should be set to `RunWorkflowById`.
- The "Command Parameter" should be the name of the KML Workflow defined in the Site (e.g. `KmlImportWorkflow`).
- Click the "Apply Changes" Button in the lower-right.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/14-apply-changes.png)

- Click the "Save Site" in the upper-right.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/15-save-site.png)

- You are now ready to launch the newly configured Site and Workflow! To load a KML or KMZ file click on the Toolbar Button in the upper-right side of the Viewer and select the new Tab and Button you created.
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/16-open-toolbar.png)
  ![](https://raw.githubusercontent.com/DigitalDataServices/KMLtoFeatureSet/master/img/17-toolbar.png)


## Usage

```
Coming soon...
```

## Change Log

List of releases and changes, with the latest at the top.

- v0.20150909
  - [FIX] When multiple geometries are loaded covering a large area, the bounding box is taken from all features and used as the basis to set the initial map extent instead of setting map extent on one particular feature.
  - [BUG] Fixed issue with XML Namespace conflicts with KML files generated by Esri ArcMap which caused XML parsing errors and prevented the KML file from being displayed.
  - [BUG] Adjusted line and polygon endpoint checks to allow non-conforming geomtries to be displayed without causing errors.
  - [BUG] Fix issue that prevented the display of HTML embedded with the <DESCRIPTION> tage with no CDATA enclosure. 

- v0.20150908
  - Initial Release

## Todo

- Attempt to parse out attribute data from within HTML in the CDATA
- Add support for rasters in KML

## Contact

**Digital Data Services, Inc.**

- [http://www.digitaldataservices.com](http://www.digitaldataservices.com)
- email: techsupport[at]digitaldataservices[dot]com

## License

Copyright (c) 2015 Digital Data Services, Inc.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
