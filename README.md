Validating-Serial--
===================

This Program validates the Serial Number 
<?php
$str ='11S71Y8150ZVQ1NM0AV021';
echo "SR# Lenght:".strlen($str)."<br>";
if(strlen($str)<=18)
{
echo "Please check the Serial#";
exit();}
else{
$first = $str[16]; echo "YY:".$first."<br>";// decode for Year
$seco = $str[17];echo "MM:".$seco."<br>";// decode for Month 
$third = $str[18];echo "DD:".$third."<br>";// decode for day
$year = array(2010=>0,2011=>1,2012=>2,2013=>3);
if(preg_match("/[0-3]/",$first)){ $first =array_search($first,$year);}
else{echo "Invalid Year"; exit();}
$month =array(1=>1,2=>2,3=>3,4=>4,5=>5,6=>6,7=>7,8=>8,9=>9,10=>'A',11=>'B',12=>'C');
if(preg_match("/[1-9]|[A-C]/",$seco)){ $seco=array_search($seco,$month);}
else{echo "Invalid Month"; exit();}
$day=array(1=>1,2=>2,3=>3,4=>4,5=>5,6=>6,7=>7,8=>8,9=>9,10=>'A',11=>'B',12=>'C',13=>'D',14=>'E',15=>'F',
           16=>'G',17=>'H',18=>'I',19=>'J',20=>'K',21=>'L',22=>'M',23=>'N',24=>'O',25=>'P',26=>'Q',27=>'R',28=>'S',29=>'T',30=>'U',31=>'V');
if(preg_match("/[1-9]|[A-V]/",$third)){ $third=array_search($third,$day);}
else{echo "Invalid Day"; exit();}
date_default_timezone_set('Europe/London');
$sample = date("$first-$seco-$third");echo "<br>";
echo "Mfd date[yy/mm/dd]:".$sample;
echo "<br>";
$validity=date('jS F Y',strtotime("$sample +39 month"));
echo "Valid upto :".$validity."<br>";
}
?> 
