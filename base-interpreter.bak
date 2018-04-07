#lang racket

(define (UofL evaluator)
   (display "UofL>")                 ; print a prompt
   (let ((expr (read)))              ; read an expression, save it in expr
      (cond ((eq? expr 'exit)        ; user asked to stop?
             (display "exiting")
             (newline))
            (else (begin                      ; otherwise,
             (write (evaluator expr))
             (newline)
             );  evaluate and print
             (UofL evaluator))))) ;  and loop to do it again

(define (math-eval expr) 
  (cond 
        ((number? expr);if the expression is just a number
         expr);return the number

        ((pair? expr) ;evaluate the expression
         (single-op-eval expr))

        ))

(define (single-op-eval expr) ;evaluates expression of type <val> <op> <val>

  (let ((op (cadr expr));second element of the 'list' that is the expression
        (val1 (math-eval (car expr)))
        (val2 (math-eval (caddr expr))))

    (cond ((eq? op '+)
            (+ val1 val2))
           ((eq? op '-)
            (- val1 val2))
           ((eq? op '*)
            (* val1 val2))
           ((eq? op '/)
            (/ val1 val2))
           ((eq? op '^)
            '(power val1 val2))
           (else
            (error "Invalid operation in expr:" expr)))))