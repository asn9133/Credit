package com.company;

import java.util.Scanner;
import java.util.ArrayList;

public class Main {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        String card_number = "";
        System.out.print("Number: ");
        card_number = input.nextLine();

        char card_digits;
        int card_digit_no;
        ArrayList<Integer> alternate_card_digit = new ArrayList<Integer>();
        for (int i = card_number.length() - 2; i >= 0; i -= 2) {
            card_digits = card_number.charAt(i);
            card_digit_no = Character.getNumericValue(card_digits);
            alternate_card_digit.add(card_digit_no);
        }

        ArrayList<Integer> card_digit_twice = new ArrayList<Integer>();
        for (int i = 0; i < alternate_card_digit.size(); i++) {
            card_digit_twice.add(alternate_card_digit.get(i) * 2);
        }

        int alternate_digit_sum = 0;
        for (int i = 0; i < card_digit_twice.size(); i++) {
            while (card_digit_twice.get(i) > 0) {
                Integer temp = card_digit_twice.get(i);
                alternate_digit_sum = alternate_digit_sum + (temp % 10);
                card_digit_twice.set(i, temp / 10);
            }
        }

        int remaining_digit_sum = 0;
        for (int i = card_number.length() - 1; i >= 0; i -= 2) {
            card_digits = card_number.charAt(i);
            card_digit_no = Character.getNumericValue(card_digits);
            remaining_digit_sum = remaining_digit_sum + card_digit_no;
        }

        int sum;
        sum = alternate_digit_sum + remaining_digit_sum;
        if (sum % 10 == 0) {

            char card_digit_character;
            int card_digit_number;

            ArrayList<Integer> credit_card_number = new ArrayList<Integer>();
            for (int i = 0; i < card_number.length(); i++) {
                card_digit_character = card_number.charAt(i);
                card_digit_number = Character.getNumericValue(card_digit_character);
                credit_card_number.add(card_digit_number);
            }

            if ((credit_card_number.size() == 15) && (credit_card_number.get(0) == 3)) {
                if ((credit_card_number.get(1) == 4) || (credit_card_number.get(1) == 7)) {
                    System.out.println("AMEX");
                } else {
                    System.out.println("INVALID");
                }
            } else if ((credit_card_number.size() == 16) && (credit_card_number.get(0) == 5)) {
                if ((credit_card_number.get(1) == 1) || (credit_card_number.get(1) == 2) || (credit_card_number.get(1) == 3) || (credit_card_number.get(1) == 4) || (credit_card_number.get(1) == 5)) {
                    System.out.println("MASTERCARD");
                } else {
                    System.out.println("INVALID");
                }
            } else if ((credit_card_number.size() == 13) || (credit_card_number.size() == 16) && (credit_card_number.get(0) == 4)) {
                System.out.println("VISA");
            } else {
                System.out.println("INVALID");
            }
        } else {
            System.out.println("INVALID");
        }
    }
}
