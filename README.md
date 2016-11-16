# OrangeHRMS

Customization of orangeHRMS for sandwhich leave pattern

This is for deducting leaves (Saturday & Sunday | National Holiday) which comes under sandwhich rule.

For example, if an employee has taken leave on Friday and Monday and in between there are two weekly offs i.e, Saturday and Sunday, then these 2 days coming in between Friday and Monday will also be counted as leaves and total leaves will be 4. 

Download OrangeHRMS
Link : https://github.com/maestrano/orangehrm/

1. Set up the whole OrangeHRMS project on the system.
2. Go and edit following file "/symfony/plugins/orangehrmLeavePlugin/lib/service/AbstractLeaveAllocationService.php"
3. Find this function "public function createLeaveObjectListForAppliedRange(LeaveParameterObject $leaveAssignmentData)"
4. Search for "$isWeekend"
   1. Commment out this line : //$isWeekend = $this->isWeekend($leaveDate, $leaveAssignmentData);
   2. Add this line instead  : $isWeekend = null;
   3. Note : if you want to apply sandwhich rule on Saturday and Sunday.
5. Search for "$isHoliday"
   1. Commment out this line : //$isHoliday = $this->isHoliday($leaveDate, $leaveAssignmentData);
   2. Add this line instead  : $isHoliday = null;
   3. Note : if you want to apply sandwhich rule on National Holiday.

Customization of orangeHRMS for sending mail (Name)

By default orangeHRMS sends email using OrangeHRM. To change the OrangeHRM sender name follow these steps.

1. Go to "/symfony/apps/orangehrm/lib/model/core/Service/EmailService.php"
2. Search for word "OrangeHRM" or "getSentAs()" in EmailService.php
3. Replace the word "OrangeHRM" with your organisation name or any suitable name.
4. You can these words on following lines
   1. 195     $this->messageFrom = array($this->emailConfig->getSentAs() => 'OrangeHRM');
   2. 466     $message->setFrom(array($this->emailConfig->getSentAs() => 'OrangeHRM'));
5. Source : http://unofficialmods.blogspot.in/2013/12/orangehrm-v301-how-to-change-email.html
6. Thank you. (If any queries : dineshsgaddi(at)gmail(dot)com )

Note : While configuring SMTP on OrangeHRMS. If someone using smtp.gmail.com. Try using port no. 465 to send mails.
