Alien
=====
import java.util.Scanner;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

import com.itextpdf.text.Document;
import com.itextpdf.text.DocumentException;
import com.itextpdf.text.Paragraph;
import com.itextpdf.text.pdf.PdfWriter;

import java.io.FileOutputStream;
import java.io.FileNotFoundException;

public class Actual {
	
		public static void main (String[] args) {
			System.out.println("Please enter the Alien details \n");
			System.out.println("Enter Alien Code Name \n");
			Scanner scan = new Scanner(System.in);
			String codename = scan.next();
			System.out.println("Enter Alien Blood Color \n");
			String bloodcolor = scan.next();
			System.out.println("Enter No. of Antennas\n");
			int antennas = scan.nextInt();
			System.out.println("Enter No. of Legs \n");
			int legs = scan.nextInt();
			System.out.println("Enter Alien Home Planet\n");
			String home = scan.next();
			String details = "Alien Details \r";
			String text = codename + bloodcolor + antennas + legs + home ;
			
			System.out.println("Please enter the format u want \n");
			System.out.println("0: for text 1: for pdf \n");
			int flag = scan.nextInt();
			
			if(flag==0)
			{
			 try {
		          File file = new File("Alien.txt");
		          BufferedWriter output = new BufferedWriter(new FileWriter(file));
		          output.write(details);
		          output.write(text);
		          output.close();
		        } catch ( IOException e ) {
		           e.printStackTrace();
		        }
			}
			else
			{
		        Document document = new Document();

		        try {
		            PdfWriter.getInstance(document,
		                new FileOutputStream("Alien.pdf"));

		            document.open();
		            document.add(new Paragraph(text));
		            document.close(); 
		        } catch (DocumentException e) {
		            e.printStackTrace();
		        } catch (FileNotFoundException e) {
		            e.printStackTrace();
		        }
		   }
		}
	}
