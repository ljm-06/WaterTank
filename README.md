import javax.swing.JOptionPane;

public class WaterTank {
    int capacity;
    int currentLevel;

    public WaterTank(int capacity) {
        this.capacity = capacity;
        this.currentLevel = 0;
    }

    public void fillTank(int liters) {
        currentLevel += liters;
        if (currentLevel > capacity) currentLevel = capacity;
        JOptionPane.showMessageDialog(null, "Level: " + currentLevel + "/" + capacity);
    }

    public void useWater(int liters) {
        currentLevel -= liters;
        if (currentLevel < 0) currentLevel = 0;
        JOptionPane.showMessageDialog(null, "Level: " + currentLevel + "/" + capacity);
    }

    public void checkStatus() {
        if (currentLevel == 0) JOptionPane.showMessageDialog(null, "Empty");
        else if (currentLevel == capacity) JOptionPane.showMessageDialog(null, "Full");
        else JOptionPane.showMessageDialog(null, "In Use");
    }

    public static void main(String[] args) {
        String choice = JOptionPane.showInputDialog("1. HomeTank (200)\n2. BuildingTank (1000)");
        int cap = choice.equals("1") ? 200 : 1000;

        WaterTank tank = new WaterTank(cap);

        while (true) {
            String action = JOptionPane.showInputDialog("1. Fill\n2. Use\n3. Status\n4. Exit");

            if (action.equals("1")) {
                int liters = Integer.parseInt(JOptionPane.showInputDialog("Liters to fill:"));
                tank.fillTank(liters);
            } else if (action.equals("2")) {
                int liters = Integer.parseInt(JOptionPane.showInputDialog("Liters to use:"));
                tank.useWater(liters);
            } else if (action.equals("3")) {
                tank.checkStatus();
            } else if (action.equals("4")) break;

            if (tank.currentLevel == 0 || tank.currentLevel == tank.capacity) {
                tank.checkStatus();
                break;
            }
        }
    }
}
[WaterTankScreenshot.pdf](https://github.com/user-attachments/files/22008241/WaterTankScreenshot.pdf)
