# job-portal<?php

$jobname=$_POST['jobname'];

$con=mysqli_connect('localhost','root');
mysqli_select_db($con,'jobs');
$q="select jobname,description,skill_req1,skill_req2 from job where jobname='$jobname'";
$result=mysqli_query($con,$q);
$num=mysqli_num_rows($result);
if($num==0){
  echo "<b>Job Not Found</b>";
}
else{
	while($row = $result->fetch_assoc()){
		echo "<b>Job Found</b> <br><br> Jobname : "  . $row['jobname']."<br> Description : ".$row['description']."<br>Skill Req 1 : ".$row['skill_req1']."<br>Skill Req 2 : ".$row['skill_req2']."<br>";
	}
}

?>
