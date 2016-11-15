# orangehrm
Customization of orangeHRMS for sandwhich leave pattern

This is for deducting leaves (Saturday & Sunday | National Holiday) which comes under sandwhich rule.

For example, if an employee has taken leave on Friday and Monday and in between there are two weekly offs i.e, Saturday and Sunday, then these 2 days coming in between Friday and Monday will also be counted as leaves and total leaves will be 4. 

Download OrangeHRMS
Link : https://github.com/maestrano/orangehrm/

1. Set up the whole OrangeHRMS project on the system.
2. Go and edit following file "orangeHRM/symfony/plugins/orangehrmLeavePlugin/lib/service/AbstractLeaveAllocationService.php"
3. Find this function "public function createLeaveObjectListForAppliedRange(LeaveParameterObject $leaveAssignmentData)"
4. Search for "$isWeekend"
   Commment out this line : //$isWeekend = $this->isWeekend($leaveDate, $leaveAssignmentData);
	 Add this line instead  : $isWeekend = null;
   Note : if you want to apply sandwhich rule on Saturday and Sunday.
5. Search for "$isHoliday"
   Commment out this line : //$isHoliday = $this->isHoliday($leaveDate, $leaveAssignmentData);
	 Add this line instead  : $isHoliday = null;
   Note : if you want to apply sandwhich rule on National Holiday.
6. Thank you. (If any queries : dineshsgaddi(at)gmail(dot)com )
