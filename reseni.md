/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package com.phonecompany.billing;

/**
 *
 * @author stehl
 */
import java.math.BigDecimal;
import java.math.BigInteger;
import java.text.ParseException;
import java.text.SimpleDateFormat;  
import java.util.Date; 
import java.util.concurrent.TimeUnit;
import java.util.logging.Level;
import java.util.logging.Logger;

public class NewClass implements TelephoneBillCalculator{
    public BigDecimal calculate(String phoneLog){
        
        BigDecimal billing = new BigDecimal(0);
        String[] calls = phoneLog.split("\n");
        
        for (String call : calls){
                try {
                SimpleDateFormat sdf = new SimpleDateFormat("DD-MM-YYYY HH:MM:SS");

                String[] portions = call.split(",");
                BigInteger number = new BigInteger(portions[0]);
                Date call_start = sdf.parse(portions[1]);
                Date call_end = sdf.parse(portions[2]);

                long durationMillies = call_end.getTime() - call_start.getTime();
                long duration = TimeUnit.MINUTES
                        .convert(durationMillies, TimeUnit.MILLISECONDS);
                
                /*
                nestíhám, 40 minut jsem válčil s NetBeans...
                
                minutovou sazbu spočítám takto:
                IF call_start  OR  call end v intervalu, najdu rozdíl
                mezi začátkem intervalu a start nebo end
                rozdíl vynásobím 1kc/min sazbou, zbytek (durr- rozíl) 0.5 kc/min
                
                ctyri moznosti (ok, zacatek v intervalu, konec v intervalu
                , oboje v intervalu), pouziju case statement
                */



            } catch (ParseException ex) {
                Logger.getLogger(NewClass.class.getName())
                        .log(Level.SEVERE, null, ex);
            }
        }
        
        return billing;     
    }
}
