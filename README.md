# JDBC
sample program for connection
package com;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class Example {

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		Class.forName("org.h2.Driver");  
		System.out.println("driver loaded successfully....");
		Connection con=DriverManager.getConnection("jdbc:h2:tcp://localhost/~/test","sa","");
		String q1="create table test(id number,name varchar2(50))";
		Statement stmt= con.createStatement();  
		int x=stmt.executeUpdate(q1);
		System.out.println("table created successfully");
		stmt.close();
		con.close();
		System.out.println("connection closed successfully");
		

	}

}
..............................................................................................................

RETRIVE THE DATA FROM DATABASE

........................................
package com;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class RetriveData {

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
        PreparedStatement p = null;
        ResultSet rs = null;
        Class.forName("org.h2.Driver");  
        Connection con=DriverManager.getConnection("jdbc:h2:tcp://localhost/~/test","sa","");
        try {
            String sql = "select * from employee";
            p = con.prepareStatement(sql);
            rs = p.executeQuery();
            while (rs.next()) {
                 int id = rs.getInt("id");
                String name = rs.getString("name");
                String place = rs.getString("place");
                System.out.println(id + "\t\t" + name
                                   + "\t\t" + place);
            }
        }
        catch (SQLException e) {
            System.out.println(e);
        }
    }
	}


