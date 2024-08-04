import javax.swing.*;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class SimpleKeylogger extends JFrame {
    private JTextArea textArea;
    private BufferedWriter bufferedWriter;

    public SimpleKeylogger() {
        // Set up the JFrame
        setTitle("Simple Keylogger");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Set up the JTextArea
        textArea = new JTextArea();
        add(new JScrollPane(textArea)); // Add JScrollPane to make it scrollable

        // Add a KeyListener to capture keystrokes
        textArea.addKeyListener(new KeyAdapter() {
            @Override
            public void keyPressed(KeyEvent e) {
                logKey(e);
            }
        });

        // Initialize the BufferedWriter
        try {
            bufferedWriter = new BufferedWriter(new FileWriter("keylog.txt", true)); // Append to the file
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Show the JFrame
        setVisible(true);
    }

    private void logKey(KeyEvent e) {
        try {
            // Log the key text (e.g., "A", "B", "Enter", etc.)
            bufferedWriter.write(KeyEvent.getKeyText(e.getKeyCode()) + " ");
            bufferedWriter.flush();
        } catch (IOException ex) {
            ex.printStackTrace();
        }
    }

    public static void main(String[] args) {
        // Create and show the GUI on the Event Dispatch Thread
        SwingUtilities.invokeLater(SimpleKeylogger::new);
    }
}
