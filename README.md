# Automaton
function autoFillAuthorizationForm(e) {
  var timestamp = e.values[0];
  var companyName = e.values[1];
  var companyAddress = e.values[2];
  var city = e.values[3];
  var pinCode = e.values[4];
  var studentFullName = e.values[5];
  var date = e.values[6];
  var dateOfInternship = e.values[7];
  var timeOfInternship = e.values[8];

  var templateFile = DriveApp.getFileById("1He7IPxDnO0UmOzDeMrl7jvMDMNMUf_-U5blU6ftQxds");
  var templateResponseFolder = DriveApp.getFolderById("13tWDDSGmmzrwnfL4an5FtPk1vpO7q3wA");

  var copy = templateFile.makeCopy(studentFullName + '.' + companyName, templateResponseFolder);

  var doc = DocumentApp.openById(copy.getId());

  var body = doc.getBody();

  body.replaceText("{{Company Name}}",companyName);
  body.replaceText("{{Company address}}",companyAddress);
  body.replaceText("{{City}}",city);
  body.replaceText("{{Pin code}}",pinCode);
  body.replaceText("{{Student FULL NAME}}",studentFullName);
  body.replaceText("{{date}}",date);
  body.replaceText("{{start and end date of internship}}",dateOfInternship);
  body.replaceText("{{time of internship}}",timeOfInternship);

  doc.saveAndClose();
  

}
