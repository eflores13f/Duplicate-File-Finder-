# Duplicate-File-Finder-

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;


public class Duplicate_File {
    //this class will be part a bigger suit

    public static void main(String[] args) {
        File dir = new File(".");
        File[] fileList = dir.listFiles();
        for (int x = 0; x < fileList.length; x++) {
            for (int y = x+1; y < fileList.length; y++) {
                if (fileList[x].length() == fileList[y].length()) {
                    if (CompareFiles(fileList[x], fileList[y])) {
                        System.out.println(fileList[y]);
                    }
                }
            }
        }

    }
}

    public static boolean CompareFiles(File x, File y) {
    try {
        FileInputStream xs = new FileInputStream(x);
        FileInputStream ys = new FileInputStream(y);
        System.out.println(" Compare: " + x + " and " + y);
        boolean result = true;
        while (result == true) {
            int xb = xs.read();
            int yb = ys.read();
            if (xs.read() !=ys.read()) {
                result = false;
                break;
            }
            return result;

        } catch (FileNotFoundException e) {
            return false;
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
        return false;

    }
    }
