### Date:       2020-September-23
### Release:    v2020092301

#### :zap: What's new

---

#### Support for Moodle Quizzes

Turnitin will be usable as a part of a Moodle quiz when Moodle releases the feature. When enabled for your account, simply add an essay question as one of the quiz questions. A similarity report will be generated when the student submits the quiz. Track this release on the [Moodle Tracker](https://tracker.moodle.org/browse/MDL-32226).

#### Privacy API declartion now includes the submission’s contents

The [Moodle Privacy API](https://docs.moodle.org/dev/Privacy_API) helps plugins report what user data a plugin uses so they cna make informed decisions about their personal information. As a part of the Privacy API declartion, we will now includethe contents of the submission to fully support the Privacy APIs goals.

Thanks to [thepurpleblob](https://github.com/turnitin/moodle-mod_turnitintooltwo/issues/464) for the catch!

#### Permission to use the Turnitin Integrity plugin can be limited to individual instructors

Two new permission settings can now be configured that will allow you to specify certain users who have access to the Turnitin Integrity plugin. This can be used to limit use to certain departments or schools within your organization.

You are now able to choose if a user is able to Enable Turnitin Integrity for an assignment, and choose if they are able to view any generated similarity reports.

You can take advantage of this new setting by navigation to Site Administration > Users > Permissions > Check system permissions for the user your wish to give access to.

#### Support for Korean, Japanese, Chinese (Traditional), and Chinese (Simplified)

Our interface has been fully localized into four new languages. Check out our help site for full step-by-step guides in these languages too

#### :wrench: Fixes and enhancements

---

#### EULA screen is now not blank after accepting the Turnitin EULA

Rather than seeing a blank screen, we’ll now show you a simple message confirming that you have accepted our EULA when navigating to <Your Moodle Instance’s URL>/plagiarism/turnitinsim/eula.php?cmd=displayeula

#### Turnitin will only show on activity types we support

Turnitin only supports Moodle assignments, forums, and workshops (and quizzes once released by Moodle!). However, it was possible that the option to enable Turnitin would show on the settings page for activity types we don't support.

To help clear up any confusion, the option to enable Turnitin will now only show on activity types we support.

---

### Date:       2020-July-21
### Release:    v2020072101

#### :zap: What's new

---

#### We now support Moodle 3.9

You can find out more about Moodle 3.9 via Moodle's [release notes](https://docs.moodle.org/dev/Moodle_3.9_release_notes).

#### EULA update notifications will no longer automatically email users

When we make an update to our EULA, we send a Moodle message to users so they can read any changes and make sure they are comfortable with them before continuing to use Turnitin. Moodle messages had defaulted to also send an email when these messages were received. After user feedback, we’ve changed how the Turnitin Integrity Plugin interacts with the Moodle Message API to default this setting to Off and making emails now opt-in.

If you’d like your users to continue getting an email when these changes happen, navigate to Site administration > Messaging > Notification settings and enable the setting for your integration.

This change will only apply to users created after this plugin update.

#### Multi-task with submissions from the same student

Students in a Moodle assignment can upload up to 20 files to the same assignment. As a part of your grading workflow, you may want to view some of these documents side-by-side to compare them directly. We’ve enabled this option so that you’ll be able to open multiple windows with submissions from the same student at the same time.

#### :wrench: Fixes and enhancements

---

#### Collusion check on Due Date

A bug had prevented some collusion checks from running on the due date. Collusion checks will now work as intended and a new report is generated for all submissions in a Moodle assignment once the due date has passed. This will only apply when the setting to regenerate on due date is turned on.

#### Resubmit link removed when a student rejects the Turnitin EULA

When a student rejects the Turnitin EULA, we provide a message saying the EULA has not been accepted rather than process the file for Similarity and return a 451 error. However, when an instructor then tried to submit a file on behalf of that student using the resubmit link, the file would be queued for processing but then return a 451 error.

Now, when a student rejects the EULA, no option to resubmit will be shown.

#### More reliable API connection check

As a part of the plugin configuration, we run a quick check of the details your provide to make sure they connection correctly to Turnitin. We’ve improved this checker to ensure that it is constantly reliable and accurately shows your connection status.

#### Turn off Turnitin for Forums and Workshops at the global level

When disabled on the global configuration page, plagiarism/turnitincheck/settings.php it had been possible to still add Turnitin to a Workshop or Forum. We’ve now made sure this setting will update the permission settings when adding one of these settings so you can turn off Turnitin when you need to.

---

### Date:      2020-April-22
### Release:   v2020042201

#### :wrench: Fixes and enhancements

---

#### Deleted files will no longer cause cron errors

We will now check a file exists before attempting to upload it to Turnitin. This check will prevent cron errors from occurring as it looks for a non-existing file.

#### Files unsuccessfully uploaded to Turnitin will now automatically retry

In the rare instance that a file is unable to be uploaded to Turnitin during submission, we will automatically retry to send it to Turnitin again without further action from the user.

#### Webhooks can now be recreated

We have fixed an issue where webhooks would not be recreated when running the “Update local configuration” scheduled task. This could cause problems when a user would try to change the URL of their Moodle instance.

---

### Date:      2020-April-17
### Release:   v2020041701

#### :wrench: Fixes and enhancements

---

#### Plugin successfully installs via zip file.

We have fixed an issue where the plugin may not install if downloaded from the Moodle plugin directory due to it containing an empty behat directory.

---

### Date:      2020-April-15
### Release:   v2020041501

#### :zap: What's new

---

#### Turnitin Integrity now available in 9 languages

You can now use all elements of the plugin using English, Danish, German, Mexican Spanish, French, Dutch, Norweigan, Brazillian Portuguese, or Swedish.

#### New user role mappings

We’ve mapped Moodle user roles more accurately with our system so we know more information about the role used when using the plugin. For example, if a teacher submits on behalf of a student, the student will now be registered as the owner of the submission but the teacher can be logged as the submitter.

#### Check for plagiarism on assignments you previously didn’t enable it for

When creating an assignment you chose if Turnitin should be enabled for it. If enabled, we’ll automatically create a Similarity Report on any files we can.

You can now retroactively enable Turnitin for an assignment, forum, or workshop, even if students have already begun to submit. You can enable Turnitin when editing an assignment by [following the usual process](https://help.turnitin.com/simcheck/integrations/moodle/instructor/assignments/adding-turnitin-to-a-moodle-assignment.htm).

#### :wrench: Fixes and enhancements

---

#### MS SQL databases are now supported

As Moodle supports MS SQL, we have changed our plugin to also offer support to prevent any potential problems when using MS SQL databases.

#### Improved retry logic for Similarity Report generation

We’ve implemented more efficient retry logic that helps to flag to customers when there is a problem with their submission sooner. After files are uploaded to Moodle we will try to generate a Similarity Report. In the vast majority of uploads this will be successful. In the rare case where report generation is not successful, we will no longer repeatedly try to generate a Similarity report. Now, the plugin will wait one hour before trying again. If after an hour the Similarity Report fails to generate, we will show an error message so the user can follow this up with our support team.
