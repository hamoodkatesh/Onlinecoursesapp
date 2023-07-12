# Onlinecoursesapp
check courses and avg of each studing if active or not . in fullstack
<?php
    require_once "DBConnection.php";
    require_once "courses.php";
    require_once "lecture.php";

    $db = new DBConnection();// מסוג משתנהDBConnection
    $index=1
?>

<!DOCTYPE html>
<html lang="en">

<head>
    <title>Table V01</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!--===============================================================================================-->
    <link rel="icon" type="image/png" href="images/icons/favicon.ico" />
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="vendor/bootstrap/css/bootstrap.min.css">
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="fonts/font-awesome-4.7.0/css/font-awesome.min.css">
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="vendor/animate/animate.css">
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="vendor/select2/select2.min.css">
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="vendor/perfect-scrollbar/perfect-scrollbar.css">
    <!--===============================================================================================-->
    <link rel="stylesheet" type="text/css" href="css/util.css">
    <link rel="stylesheet" type="text/css" href="css/main.css">
    <!--===============================================================================================-->
</head>

<body>
    <div class="limiter">
        <div class="container-table100">
            <div class="wrap-table100">
                <div class="table100">
                <h1>Courses Pages</h1>
                    <h2>Click on name of course</h2>
                    <table>
                        <thead>
                            <tr class="table100-head">
                                <th class="column1">ID</th>
                                <th class="column2">Course Name</th>
                                <th class="column3">Status</th>
                            </tr>
                        </thead>
                        <?php $res = $db->getAllCoures();?>
                        <tbody>
                            <?php while($row = $res->fetch(PDO::FETCH_ASSOC)):
                            {
                                        $id=$row['id_course'];
                                        $name=$row['course_name'];
                                        $status=$row['course_status'];
                                        $bg_color = 'palegreen';
                                        if($status == 0)
                                            $bg_color = 'white';
                            }?>
                            <tr style="background-color: <?php echo $bg_color ?>">
                                <td class="column1"><?php echo $id;?></td>
                                <td class="column2"><a href="lecturePage.php?id_course=<?php echo $id;?>"><button type="course_name" class=" btn btn-primary"><?php echo $name;?></button></a></td>
                                <td class="column3"><?php echo $status;?></td>
                            </tr>
                            <?php endwhile;?>
                        </tbody>
                        
                    </table>
                </div>
            </div>
        </div>
    </div>


    <!--===============================================================================================-->
    <script src="vendor/jquery/jquery-3.2.1.min.js"></script>
    <!--===============================================================================================-->
    <script src="vendor/bootstrap/js/popper.js"></script>
    <script src="vendor/bootstrap/js/bootstrap.min.js"></script>
    <!--===============================================================================================-->
    <script src="vendor/select2/select2.min.js"></script>
    <!--===============================================================================================-->
    <script src="js/main.js"></script>

</body>

</html>
