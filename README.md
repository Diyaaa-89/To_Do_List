# To_Do_List
#To Do List using python


   String[] questions = {"1 + 1 = ?","3 - 3 = ?","5 + 5 = ?","10 X 9 = ?","100 - 50 = ?"};
    // create an array of options
    // the last item is the correct answer
    // we will check the selected answer from the user with the last item
    String[][] options = {{"100","9","2","0","2"},{"15","7","0","11","0"},{"20","10","50","5","10"},{"80","70","90","100","90"},{"60","50","40","25","50"}};

    // index to display the next question, correct to count the correct answers
    int index = 0, correct = 0;

    // button group to contain the radiobuttons
    ButtonGroup bg = new ButtonGroup();
    
   
public Quiz_Form() {
        initComponents();
        
// add the radiobuttons to the button group 
        bg.add(jRadioButton1_);
        bg.add(jRadioButton2_);
        bg.add(jRadioButton3_);
        bg.add(jRadioButton4_);
        
        jButton_Next_QActionPerformed(null);
    }


    public void getSelectedOption(JRadioButton rbtn)
    {
        // get the selected value from the radiobutton
        // increment the index
        // disable the radiobuttons
        // check if the user selected the right answer
        System.out.println(rbtn.getText());
        System.out.println(options[index][4]);

        if(rbtn.getText().equals(options[index][4]))
        {
            correct++;
        }
        index++;
        enableRbuttons(false);
    }


    // enable/ disable radiobuttons
    public void enableRbuttons(boolean yes_or_no)
    {
        jRadioButton1_.setEnabled(yes_or_no);
        jRadioButton2_.setEnabled(yes_or_no);
        jRadioButton3_.setEnabled(yes_or_no);
        jRadioButton4_.setEnabled(yes_or_no);
    }


    private void jButton_Next_QActionPerformed(java.awt.event.ActionEvent evt) {                                               
        
        if(jButton_Next_Q.getText().equals("Restart The Quiz"))
        {
            // restart the quiz
            jButton_Next_Q.setText("Next");
            jPanel_Q_Container.setBackground(new java.awt.Color(204, 204, 204));
            index = 0;
            correct = 0;
        }
        
        if(index == questions.length)
        {
            // display the user score
            Lbl_Question.setText("Your Score: " + correct + " / " + questions.length);
            if(correct >= (float) questions.length/2)
            {
               jPanel_Q_Container.setBackground(Color.green);
            }
            else{
                jPanel_Q_Container.setBackground(Color.red);
            }
            
            jButton_Next_Q.setText("Restart The Quiz");
        }
        
        else{
               // enable radio buttons
             enableRbuttons(true);

             // display the next question
             Lbl_Question.setText(questions[index]);
             jRadioButton1_.setText(options[index][0]);
             jRadioButton2_.setText(options[index][1]);
             jRadioButton3_.setText(options[index][2]);
             jRadioButton4_.setText(options[index][3]);
             
             if(index == questions.length-1){
                 jButton_Next_Q.setText("Finish and See The Result");
             }
            
        }
        
        // clear the selection
        bg.clearSelection(); 
        
    }                                              

    private void jRadioButton1_ActionPerformed(java.awt.event.ActionEvent evt) {                                               
        getSelectedOption(jRadioButton1_);
    }                                              

    private void jRadioButton2_ActionPerformed(java.awt.event.ActionEvent evt) {                                               
        getSelectedOption(jRadioButton2_);
    }                                              

    private void jRadioButton3_ActionPerformed(java.awt.event.ActionEvent evt) {                                               
        getSelectedOption(jRadioButton3_);
    }                                              

    private void jRadioButton4_ActionPerformed(java.awt.event.ActionEvent evt) {                                               
        getSelectedOption(jRadioButton4_);
    }                                              
