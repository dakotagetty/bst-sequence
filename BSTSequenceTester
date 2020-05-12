import components.sequence.Sequence;
import components.sequence.Sequence1L;
import components.simplereader.SimpleReader;
import components.simplereader.SimpleReader1L;
import components.simplewriter.SimpleWriter;
import components.simplewriter.SimpleWriter1L;

/**
 * Program to analyze a sequence of integer keys against the search for a node
 * within a Binary Search Tree.
 *
 * @author Dakota Getty
 *
 */
public final class BSTSequenceTester {

    /**
     * Private constructor so this utility class cannot be instantiated.
     */
    private BSTSequenceTester() {
    }

    /**
     * Runs each entry in the sequence through a series of logic tests to
     * determine if the order can mimic a binary search tree branch. Recursion
     * is utilized due to the stacking of the tests throughout the algorithm.
     *
     * @param s
     *            The sequence of integer keys.
     * @param z
     *            The integer that is being searched for.
     * @return True if the sequence travels successfully to the end key. False
     *         otherwise.
     */
    public static boolean testSequence(Sequence<Integer> s, int z) {
        // The first number of the sequence is assigned to start
        int start = s.entry(0);
        // didBreak assists with the logic through the traversal of the sequence.
        boolean didBreak = false;
        // The return variable
        boolean success = false;

        /*
         * Base case test in the instance that the sequence is of length one.
         */
        if (start == z) {
            return true;
        }

        /*
         * The initial if/else determines whether the start of the sequence is
         * greater than or less than the goal key. Each block within the
         * statement is mirrored with the exception of logic signs being
         * flipped.
         */
        int x = 0;
        if (z > start) {
            /*
             * The while loop increments through s until the next entry in s is
             * greater than the current or the end z is reached.
             */
            while (s.entry(x) != z && s.entry(x + 1) > s.entry(x)) { // Short circuiting prevents out of bounds error when reaching z at end of sequence.
                x++;
                // checks if at the end of the sequence and halts the loop.
                if (x == s.length() - 1) {
                    didBreak = true;
                    break;
                }
            }
            /*
             * The way the sequence fails to represent a binary tree occurs here
             * when the next entry being observed (relative to integer x) is
             * less than start.
             */
            if (!didBreak && s.entry(x + 1) < start) { // didBreak prevents out of bounds error
                success = false;
            } else {
                /*
                 * If no failure occured, a new sequence temp ranging from x to
                 * z is created and testSequence is recursively called on temp.
                 */
                Sequence<Integer> temp = s.newInstance();
                s.extract(x, s.length(), temp);
                success = testSequence(temp, z);
            }
        } else {
            while (s.entry(x) != z && s.entry(x + 1) < s.entry(x)) {
                x++;
                if (x == s.length() - 1) {
                    didBreak = true;
                    break;
                }
            }
            if (!didBreak && s.entry(x + 1) > start) {
                success = false;
            } else {
                Sequence<Integer> temp = s.newInstance();
                s.extract(x, s.length(), temp);
                success = testSequence(temp, z);
            }
        }
        return success;
    }

    /**
     * Main method.
     *
     * @param args
     *            the command line arguments
     */
    public static void main(String[] args) {
        // Open the input and output streams.
        SimpleReader in = new SimpleReader1L();
        SimpleWriter out = new SimpleWriter1L();

        /*
         * Declaration of sequence data structure to hold the keys to be
         * examined.
         */
        Sequence<Integer> test = new Sequence1L<>();

        /*
         * z holds the key that the user needs to search for. Each key is added
         * to test in order provided by the input.
         */
        int z = 363;
        test.add(0, 2);
        test.add(1, 250);
        test.add(2, 401);
        test.add(3, 398);
        test.add(4, 330);
        test.add(5, 344);
        test.add(6, 297);
        test.add(7, 363);

        /*
         * The first part of the output is printed which is simply an output of
         * the keys in order.
         */
        out.print("The sequence ");
        for (int i = 0; i < test.length(); i++) {
            out.print(test.entry(i));
            if (i != test.length() - 1) {
                out.print(", ");
            }
        }

        /*
         * testSequence is called with sequence test and integer z as the two
         * parameters, respectively. The output assigns the boolean path
         * accordingly after examining the sequence.
         */
        boolean path = testSequence(test, z);

        if (path) {
            out.print(" can ");
        } else {
            out.print(" cannot ");
        }
        out.print("be the sequence of keys examined during the search for " + z
                + " in a binary search tree.");

        // Close the input and output streams.
        in.close();
        out.close();
    }

}
