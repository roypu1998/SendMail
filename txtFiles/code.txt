package com.sendemail;

/*
 * Before you using in this application
 * you need change your email access 
 * settings at low security 
 * levels to make the program work
 */


import java.util.Properties;

import javax.mail.Message;
import javax.mail.MessagingException;
import javax.mail.PasswordAuthentication;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class SendEmails {
	JFrame frame;
	JLabel titel;
	JLabel sendFrom;
	JLabel password;
	JLabel nameReceiver;
	
	JLabel to;
	JLabel msg;
	final JTextField sendEmaillFrom;
	final JPasswordField passwordText;
	final JTextField nameReceiverText;
	final JTextField emailText;
	final JTextArea msgText;
	JButton submit;
	JMenuBar menuBar;
	JMenu file;
	JMenu about;
	JMenuItem ex;
	JMenuItem development;
	JFrame aboutframe;
	
	public SendEmails() {
		titel=new JLabel(" Send Email ",SwingConstants.CENTER);
		sendFrom=new JLabel("Your Email Address");
		password=new JLabel("Your Email Password");
		sendEmaillFrom=new JTextField();
		passwordText=new JPasswordField(20);
		
		nameReceiver=new JLabel("Name Of The Receiver : ");
		to=new JLabel("Send To : ");
		msg=new JLabel("Message ");
		nameReceiverText=new JTextField();
		emailText=new JTextField();
		msgText=new JTextArea("Write Here...");
		submit=new JButton("Send");
		
	}

	public void createFrame() {
		frame=new JFrame("Send Email");
		menuBar=new JMenuBar();
		frame.setJMenuBar(menuBar);
		buildMenu();
		SendEmails app=new SendEmails();
		Component components=app.createComponents();
		frame.getContentPane().add(components,BorderLayout.CENTER);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.pack();
		frame.setVisible(true);
	}
	
	public void buildMenu() {
		
		file=new JMenu("File");
		about=new JMenu("About");
		ex=new JMenuItem("Exit");
		development=new JMenuItem("Development");
		file.add(ex);
		about.add(development);
		menuBar.add(file);
		menuBar.add(about);
		ex.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e) {
            	System.exit(0);
            }
		});
		
		development.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e) {
            	createFrameAbout();
            }
		});
	}
	
	
	public void createFrameAbout() {
		aboutframe=new JFrame("Development");
		JLabel devloper=new JLabel("Developer: ");
		JLabel mailofdev=new JLabel("Mail: ");
		JLabel thedev=new JLabel("Roi Putterman");
		JLabel themail=new JLabel("royputterman@gmail.com"); 
		JPanel panelA=new JPanel();
		panelA.setBorder(BorderFactory.createEmptyBorder(10,10,10,10));
		panelA.setLayout(new GridLayout());
		panelA.setBackground(Color.BLACK);
		JPanel panelabout=new JPanel();
		panelabout.setBorder(BorderFactory.createEmptyBorder(5,5,5,5));
		panelabout.setBackground(Color.WHITE);
		GridLayout layoutabout=new GridLayout(2,2);
		layoutabout.setVgap(5);
		layoutabout.setHgap(5);
		panelabout.setLayout(layoutabout);
		panelabout.add(devloper);
		panelabout.add(thedev);
		panelabout.add(mailofdev);
		panelabout.add(themail);
		panelA.add(panelabout);
		aboutframe.getContentPane().add(panelA,BorderLayout.CENTER);
		aboutframe.setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
		aboutframe.pack();
		aboutframe.setVisible(true);
	}
	
	public Component createComponents() {
		
		titel.setForeground(Color.BLUE);
		titel.setFont(new Font("Serif", Font.TYPE1_FONT, 100));
		nameReceiverText.setBackground(Color.LIGHT_GRAY);
		emailText.setBackground(Color.LIGHT_GRAY);
		msgText.setBackground(Color.LIGHT_GRAY);
		sendEmaillFrom.setBackground(Color.LIGHT_GRAY);
		passwordText.setBackground(Color.LIGHT_GRAY);
		//main panel//
		JPanel main=new JPanel();
		main.setLayout(new BoxLayout(main, BoxLayout.Y_AXIS));
		main.setBorder(BorderFactory.createEmptyBorder(10,10,10,10));
		main.setBackground(Color.WHITE);
		
		
		JPanel panelTitel=new JPanel();
		panelTitel.setBorder(BorderFactory.createEmptyBorder(10, 10, 50, 10));
		panelTitel.setBackground(Color.WHITE);
		panelTitel.setLayout(new GridLayout(1,1));
		panelTitel.add(titel,BorderLayout.SOUTH);
		
		//panel of entering details// 
		JPanel p1=new JPanel();
		p1.setBorder(BorderFactory.createEmptyBorder(5, 10, 30, 10));
		p1.setBackground(Color.WHITE);
		GridLayout layout1=new GridLayout(4,2);
		layout1.setVgap(15);
		layout1.setHgap(15);
		p1.setLayout(layout1);
		
		p1.add(sendFrom);
		p1.add(sendEmaillFrom);
		p1.add(password);
		p1.add(passwordText);
		p1.add(nameReceiver);
		p1.add(nameReceiverText);
		p1.add(to);
		p1.add(emailText);
		
		
		JPanel messagePanel=new JPanel();
		messagePanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 50, 10));
		messagePanel.setBackground(Color.WHITE);
		GridLayout layout3=new GridLayout(2,1);
		messagePanel.setLayout(layout3);
		msgText.setPreferredSize(new Dimension(100,1000));
		messagePanel.add(msg);
		messagePanel.add(msgText);
		
		
		//submit button//
		JPanel p2=new JPanel();
		p2.setBorder(BorderFactory.createEmptyBorder(10, 10, 50, 10));
		p2.setBackground(Color.WHITE);
		GridLayout layout2=new GridLayout(3,1);
		layout2.setVgap(30);
		p2.setLayout(layout2);
		p2.add(submit);
		submit.setMnemonic(KeyEvent.VK_ENTER);
		submit.addActionListener(new ActionListener(){
            public void actionPerformed(ActionEvent e) {
            	
            	 String to = emailText.getText();

                 // Sender's email ID needs to be mentioned
                 String from = sendEmaillFrom.getText();

                 // Assuming you are sending email from through Gmails smtp
                 String host = "smtp.gmail.com";

                 // Get system properties
                 Properties properties = System.getProperties();

                 // Setup mail server
                 properties.put("mail.smtp.host", host);
                 properties.put("mail.smtp.port", "465");
                 properties.put("mail.smtp.ssl.enable", "true");
                 properties.put("mail.smtp.auth", "true");

                 // Get the Session object.// and pass username and password
                 Session session = Session.getInstance(properties, new javax.mail.Authenticator() {

					protected PasswordAuthentication getPasswordAuthentication() {

                         return new PasswordAuthentication(sendEmaillFrom.getText(), passwordText.getText());

                     }

                 });

                 // Used to debug SMTP issues
                 session.setDebug(true);

                 try {
                     // Create a default MimeMessage object.
                     MimeMessage message = new MimeMessage(session);

                     // Set From: header field of the header.
                     message.setFrom(new InternetAddress(from));

                     // Set To: header field of the header.
                     message.addRecipient(Message.RecipientType.TO, new InternetAddress(to));

                     // Set Subject: header field
                     message.setSubject("Java Applictation Test");

                     // Now set the actual message
                     message.setText("This Message From "+sendEmaillFrom.getText()+"\nHello "+nameReceiverText.getText()+" "+"\n"+msgText.getText());

                     System.out.println("sending...");
                     // Send message
                     Transport.send(message);
                     System.out.println("Sent message successfully....");
                 } catch (MessagingException mex) {
                     mex.printStackTrace();
                 }
            
            } 
            
		});
		
		
		main.add(panelTitel);
		main.add(p1);
		main.add(messagePanel);
		main.add(p2);
		return main;
		
	}
	
	
	public static void main(String[] args) {
		SendEmails sendemail=new SendEmails();
		sendemail.createFrame();
		
	}
}
