/*
Nick Croucher
Lab 7
*/
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.BufferedWriter;
import java.io.FileInputStream;
import java.io.FileWriter;

public class name_database extends javax.swing.JFrame 
{
    static String names [];
    
    /**
     * Creates new form name_database
     */
    public name_database() {
        initComponents();
    }

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        search_button = new javax.swing.JButton();
        JScrollPane1 = new javax.swing.JScrollPane();
        results_area = new javax.swing.JTextArea();
        search_box = new javax.swing.JTextField();
        add_box = new javax.swing.JTextField();
        add_button = new javax.swing.JButton();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        search_button.setText("Search");
        search_button.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                search_buttonActionPerformed(evt);
            }
        });

        results_area.setColumns(20);
        results_area.setRows(5);
        JScrollPane1.setViewportView(results_area);

        search_box.setText("Insert Names to Search");
        search_box.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                search_boxActionPerformed(evt);
            }
        });

        add_box.setText("Insert Names to Add");
        add_box.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                add_boxActionPerformed(evt);
            }
        });

        add_button.setText("Add Names");
        add_button.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                add_buttonActionPerformed(evt);
            }
        });

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                .addGap(0, 26, Short.MAX_VALUE)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                        .addComponent(JScrollPane1, javax.swing.GroupLayout.PREFERRED_SIZE, 244, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addGap(434, 434, 434))
                    .addGroup(layout.createSequentialGroup()
                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addComponent(add_box, javax.swing.GroupLayout.PREFERRED_SIZE, 175, javax.swing.GroupLayout.PREFERRED_SIZE)
                            .addComponent(search_box, javax.swing.GroupLayout.PREFERRED_SIZE, 175, javax.swing.GroupLayout.PREFERRED_SIZE))
                        .addGap(36, 36, 36)
                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING, false)
                            .addComponent(add_button, javax.swing.GroupLayout.DEFAULT_SIZE, 169, Short.MAX_VALUE)
                            .addComponent(search_button, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                        .addContainerGap(javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))))
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addComponent(JScrollPane1, javax.swing.GroupLayout.PREFERRED_SIZE, 239, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(search_box, javax.swing.GroupLayout.PREFERRED_SIZE, 44, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(search_button, javax.swing.GroupLayout.PREFERRED_SIZE, 44, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(40, 40, 40)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(add_box, javax.swing.GroupLayout.PREFERRED_SIZE, 46, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(add_button, javax.swing.GroupLayout.PREFERRED_SIZE, 46, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addContainerGap(87, Short.MAX_VALUE))
        );

        pack();
    }// </editor-fold>                        

    private void search_buttonActionPerformed(java.awt.event.ActionEvent evt) {                                              
      array_population();
      results_area.setText("");
      for (int loop_counter=0; loop_counter < names.length; loop_counter++) 
      {
          if (names[loop_counter].toUpperCase().contains((CharSequence)search_box.getText().toUpperCase()))
          {
              results_area.append(names[loop_counter] + "\n");
          }    
      }  
      
    }                                             

    private void search_boxActionPerformed(java.awt.event.ActionEvent evt) {                                           
        // TODO add your handling code here:
    }                                          

    private void add_buttonActionPerformed(java.awt.event.ActionEvent evt) {                                           
    try
    {
        BufferedWriter bw = new BufferedWriter(new FileWriter("name_list.txt", true));
        bw.newLine();
        bw.write(add_box.getText());
        bw.close();
    }
    catch (IOException E)
    {
        System.out.println(E);
    }
    add_box.setText("Enter Another Name");
    }                                          
    private void add_boxActionPerformed(java.awt.event.ActionEvent evt) {                                        
        // TODO add your handling code here:
    }                                       
   
    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) throws IOException 
    {
        java.awt.EventQueue.invokeLater(new Runnable() 
        {
            public void run() 
            {
                new name_database().setVisible(true);
            }
        });
        array_population();
    }
    static void array_population()
    {
        String entry;
        int counter = 0;
        int people = 0;
        
        try
        {
            FileInputStream fis = new FileInputStream("name_list.txt");
            BufferedReader input = new BufferedReader (new InputStreamReader(fis));
            while (input.readLine() != null)
            {
                counter++;
            }            
            input.close();
            fis.close();
            names = new String[counter];
            
            fis = new FileInputStream("name_list.txt");
            input = new BufferedReader (new InputStreamReader(fis));
            while ((entry = input.readLine()) != null)
            {
                names[people] = entry;
                people++;
            }
            input.close();
            fis.close();
        }
        catch (IOException E)
        {
            System.out.println(E);
        }
                     
            /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(name_database.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(name_database.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(name_database.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(name_database.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
    }
    
    // Variables declaration - do not modify                     
    private javax.swing.JScrollPane JScrollPane1;
    private javax.swing.JTextField add_box;
    private javax.swing.JButton add_button;
    private javax.swing.JTextArea results_area;
    private javax.swing.JTextField search_box;
    private javax.swing.JButton search_button;
    // End of variables declaration                   
}
