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
