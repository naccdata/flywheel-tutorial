# ADRC Data in Flywheel User Interface

Orientation to how ADRC data is stored in Flywheel, and the basics of using the Flywheel interface.

Note: this tutorial not cover the portal interface.

## Preliminaries

### Get Google Chrome Browser

Flywheel is built to work best on the Chrome browser.
So, if you are going to use Flywheel often, you should install [Chrome](google.com/chrome).

### Login

1. In Google Chrome, go to [flywheel.naccdata.org](https://flywheel.naccdata.org).
2. Click the button "University Credentials via CILogon"
3. Under "Select an Identity Provider" choose "University of Washington" and click the "Log On" button.
4. You should be taken to the UW login page and be asked to login using 2FA.
5. You should arrive at the Projects page of Flywheel, which has a list of the projects to which you have access.

## Data organization

Flywheel uses a hierarchical data organization.
The top of the hierarchy is the *site*, which is the system you are logged into.
Next is group, which contains projects.

Each ADRC has a group, and a number of projects.

The project page shows you all of the projects to which you have access, which could potentially be a long list.
So, you will want to use the interface to find what you want.

### Center Data

1. *Use the Group text box to search for "Mount Sinai"*

   There is a group for each ADRC -- in this case Mount Sinai.

   Under Mount Sinai, you see projects named "accepted", "ingest-form", "ingest-scan", and "retrospective-form".
   These projects correspond to phases in the data pipeline:

   - `ingest` projects are data type specific, and hold submitted data.
     For instance, "ingest-form" holds any submitted form data.
     The project "ingest-scan" is data from the SCAN project pulled from LONI.
   - `retrospective` projects hold already QC'd data from prior systems.
   - `accepted` projects hold all "curated" data, which has passed QC.

   If you are answering questions about what data is in the system, you would look in retrospective to see any form data from the "current" database, "ingest" for data from the new submission system, and "accepted" to see data that has passed QC and is available for inclusion in snapshots.

2. *Click on the "accepted" project for Mount Sinai*

   This will take you to the *Description* tab for the accepted project.

   A couple of things to notice:

   1. Each project has a reference, which you can see at the top of the page, next to the word "accepted".
   For this project it is `fw://mount-sinai/accepted`.
   This reference can be used to find projects when scripting.
   2. The page has multiple tabs related to the data in this project.
   Sessions and Subjects are different ways to get to participant data.

### Participant Data

1. *From within the accepted project, click on the "Subjects" tab*

   This tab shows you the list of participants with data from Mt Sinai that has passed QC.

   Click on a row with a NACCID.

   This will open the "Subject" tab, which has participant metadata that has been scraped from the UDS forms.

   There is also additional custom information labeled 'cognitive', 'demographics' and 'enrollment' which have metadata computed from the forms of the participant.

   Notice that each NACCID has a bubble with a count next to it.
   This is the number of sessions attached to the participant.

2. *Pick a NACCID from the list on the left, and type it into the "Subject label" box, and then click "Sessions" for that subject.*

   This filtering could be used to find the accepted data for a particular NACCID.

   This view will show all the data for the participant with that NACCID within the accepted project.

   Note: A session in this context is an event where data is collected.

   With the current data, you may see sessions which are forms for a particular visit, or milestone forms.
   A UDSv3 session will have medicines split as a separate file.

   Using the "Session label" box, you can filter participants by the label of the session.
   Clear the NACCID from the "Subject label" box, and type `milestone`
   in the "Session label" to see participants with milestone forms.

3. *Select a file in one of the sessions. Hover your mouse over the file name and click the "picture frame" icon that appears*

   The "picture frame" icon throughout Flywheel launches a data viewer.
   In this case, we have JSON data files, and the viewer is a simple interface that we built to make the data easier to read.

   If you want to see the source data, click the vertical elipses to the right and choose "Launch in Code Editor".
   *We have permissions set so that you cannot change data files directly.*

### Project data

1. *Go to the "ingest-scan" project for Mount Sinai*

   Yes, this is a test.

2. *Click the "Information" tab.

   At the top of the tab is "Applications", which has the link for the SCAN Dashboard for Mount Sinai.
   Clicking this link will open the dashboard interface.

   The data files for the dashboard are attached to this project, and are visible in the "Attachments" section for the tab.

3. *However over a file in attachments, click the vertical ellipses, and select "Launch in Tabular Data".*

   Tabular Data is another data viewer that shows a CSV in tabular form.

   Note that the actions menu also allow other steps with the file, including downloading.

4. *In the attachements list, click the blue box with the count next to one of the files*

   Files are versioned in Flywheel; the blue box next to the file name shows the version.
   Clicking the blue box opens a dialog allowing you to access previous versions of the file.

## Searching for Data

Flywheel also supports searching for data.

1. *Click "Search" at the top of the left hand menu*

   This will take you to the "Basic Search" page, which allows you to filter subjects using the checkboxes on the left.

   The "PROJECT" field determines which project will be used for the search.
   If you click search while viewing a particular project, the search will be restricted to that project.
   You can change the project, or choose none, using the dropdown box.

   > You have to click "Exit Search" to go back to the regular menu.

2. *Click "Advanced Search"*

   The advanced search allows us to construct more complex queries.

   On the right is a "visual editor" that we can used to create search queries.

   In the "Field" box of the visual editor type `birthyr` (lowercase, please).
   This will fill out the complete field name, which is `file.info.forms.json.birthyr`.
   This field is in the Flywheel metadata but represents the `birthyr` variable from the UDS form.

   The editor will recognize that `birthyr` is a numeric value and allow you to create a range query.
   Fill in the min and max of the range, and the search term should appear in the query box on the left of the page.

   Add a search term by clicking "Add Term".
   Type `cdrsum`, and select `file.info.forms.json.cdrsum` and set "Min" to 2 leaving "Max" blank.

   The query box should have the following query

   ```text
   file.info.forms.json.birthyr >= 1950 AND file.info.forms.json.birthyr <= 2000 AND file.info.forms.json.cdrsum >= 2
   ```

   Click "Run Query", and you will see a list of results.

   Remember to exit the search mode.

## Tabular data views

We can create tabular data views within Flywheel, but we aren't going to get too deep into this capability here.

1. *Get back to the Mount Sinai "accepted" project*

   Yes, this is also a test.

2. *Click the "Data Views" tab, then click "Queue"*

    Wait! Don't click the "participant details" link!

3. *Click the eye "view data" icon*

   This shows a tabular view of data gathered for participants in the Mount Sinai accepted project.
   These are the "custom information" fields that we saw attached to a participant earlier.

   This data can be downloaded here or through the Flywheel API.

## Resources

[Flywheel Documenation](https://docs.flywheel.io/)