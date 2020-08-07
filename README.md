# Control_panel_Tracking
Here you will find code for Html + CSS + Php to devlop a control system to track robot movement with manage (SQL) query  

The project here includes a control panel for movement of robot. Controlling will be through 4 buttons:
*first option is save:
which recording movement of robot and save it into database by query:

if(isset($_POST["save"])){

	$sql="INSERT INTO `control__system` (`ID`, `Room_name`, `Forward`, `Turn_right`, `Turn_left`) 
	VALUES (NULL, $room_name, $forward, $Rright, $Lleft)" ;

  if($conn->query($sql)===TRUE){
    echo "Data added successfully";
  }
  else{
    echo "Error ".$sql.$conn->error;
  }
}

*second option is disply the contents of databse as (ID, Name):

  if(isset($_POST["view"])){

  $sql= "SELECT ID,Room_name FROM control__system ";
  $result = mysqli_query($conn, $sql);
  if (mysqli_num_rows($result) > 0) {
  	while($row=mysqli_fetch_assoc($result)){
  		
  		echo "No. : ".$row["ID"]."<pre>";
  		echo "Room_name :".$row['Room_name']."<pre>";

    }
}
}

*third option is for modification;
if you want to delete entered data, just you have to enter the number of 'ID' of this data:

  if(isset($_POST["del"])){

    $sql="DELETE FROM control__system WHERE `ID`=$d";
    if($conn->query($sql)===TRUE){
    echo "Data deleted successfully";
}
  else{
    echo "Error ".$sql.$conn->error;
  }
}

*Finally,
draw the robot movement path on the screen based on entered value:

 if(isset($_POST["start"])){

  	echo "Space for Tracking Robot Movement"."<br>";
  	echo '<svg height="300" width="300" style="background-color:#E9967A">
  	<path d="M 0,0 L20,'.$forward.'  '.$Rright.' '.$Lleft.',0 z stroke-width:10" />
    </svg>';
 }



