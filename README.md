package Test;

import DBM.*;

public class MemberListQuery
{
    
    public String getMemberListNameQuery(String ID, String DateFrom, String DateTo)
    {
        String query = "SELECT DISTINCT concat(u.givenname, \" \", u.surname)\n" +
        "FROM fos_user u\n" +
        "JOIN dts_timesheet t\n" +
        "ON u.id=t.user_id\n" +
        "JOIN pworeg_project_member p\n" +
        "ON u.id=p.member_id\n" +
        "JOIN pworeg_project w\n" +
        "ON p.proj_id=w.id\n" +
        "WHERE w.id=" + ID + "\n" +
        "AND t.date >= '" + DateFrom + "'\n" +
        "AND t.date <= '" + DateTo + "'\n" +
        "ORDER BY t.date;";
        return query;
    }
    
    public String getMemberListDateQuery(String ID)
    {
        String query = "SELECT DISTINCT t.date\n" +
        "FROM fos_user u\n" +
        "JOIN dts_timesheet t\n" +
        "ON u.id=t.user_id\n" +
        "JOIN pworeg_project_member p\n" +
        "ON u.id=p.member_id\n" +
        "JOIN pworeg_project w\n" +
        "ON p.proj_id=w.id\n" +
        "WHERE w.id=" + ID + "\n" +
        "ORDER BY t.date;";
        return query;
    }
    
    public String getMemberListDatePeriodQuery(String ID, String DateFrom, String DateTo)
    {
        String query = "SELECT DISTINCT t.date\n" +
        "FROM fos_user u\n" +
        "JOIN dts_timesheet t\n" +
        "ON u.id=t.user_id\n" +
        "JOIN pworeg_project_member p\n" +
        "ON u.id=p.member_id\n" +
        "JOIN pworeg_project w\n" +
        "ON p.proj_id=w.id\n" +
        "WHERE w.id=" + ID + "\n" +
        "AND t.date >= '" + DateFrom + "'\n" +
        "AND t.date <= '" + DateTo + "'\n" +
        "ORDER BY t.date;";
        return query;
    }
    
    public String getMemberListHoursQuery(String ID, String Name, String Date)
    {
        String query = "SELECT COALESCE(NULLIF(t.dailyHours,''), 'No Data')\n" +
        "FROM fos_user u\n" +
        "JOIN dts_timesheet t\n" +
        "ON u.id=t.user_id\n" +
        "JOIN pworeg_project_member p\n" +
        "ON u.id=p.member_id\n" +
        "JOIN pworeg_project w\n" +
        "ON p.proj_id=w.id\n" +
        "WHERE concat(u.givenname, \" \", u.surname)='" + Name + "'\n" +
        "AND date='" + Date + "'\n" +
        "AND w.id=" + ID + "\n" +
        "ORDER BY t.date;";
        return query;
    }
    
}
