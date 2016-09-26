# hw

var
    fin, fout: text;
    n, i, j: byte;
    a: array[1..100] of word;
    s: array[1..100] of word;
    x: word;

begin
    assign(fin, 'input.txt');
    assign(fout, 'output.txt');
    reset(fin);
    rewrite(fout);
    readln(fin, n);
    for i := 1 to n do
    begin
        read(fin, a[i]);
        s[i] := a[i] mod 10 + (a[i] div 10) mod 10 + a[i] div 100;
    end;
    for i := 1 to n - 1 do
    begin
        for j := n - 1 downto i do
            if (s[j + 1] < s[j]) then
            begin
                x := a[j + 1];
                a[j + 1] := a[j];
                a[j] := x;
            end;
    end;
    for i := 1 to n do
        write(fout, a[i], ' ');
    close(fin);
    close(fout);
end.
