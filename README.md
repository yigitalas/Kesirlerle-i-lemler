# Kesirlerle-i-lemler
c++ Kesirlerle işlemler yapmaya çalışıyorum fakat değerler beklediğim gibi çıkmıyor hatamı bulamıyorum...


Kod şu şekilde ;

#include <iostream>
using Sayi = int;

class Kesirler {
private:
    Sayi _pay;
    Sayi _payda;
public:
    Kesirler() {
        _pay = 0;
        _payda = 0;
    }
    Kesirler(Sayi pay, Sayi payda) {
        _pay = pay;
        _payda = payda;
    }
friend std::ostream& operator<<(std::ostream& cikti,const Kesirler &sayi);
friend std::istream& operator>>(std::istream& girdi, Kesirler& sayi);
Kesirler operator+( Kesirler toplanan) {
    Kesirler toplam;
    if (_payda !=toplanan._payda ){
        _pay= _pay * toplanan._payda;
        toplanan._pay = toplanan._pay * _payda;
        toplam._pay = toplanan._pay + _pay;
        toplam._payda= _payda * toplanan._payda;
        return toplam;
    }
    else;{
        toplam._pay = toplanan._pay + _pay;
        toplam._payda = toplanan._payda;
        return toplam;
    }
    return toplam;
}
Kesirler operator-(Kesirler cikartilan) {
    Kesirler cikan;
    if (_payda != cikartilan._payda ) {
        cikan._payda = _payda * cikartilan._payda;
        cikartilan._pay = cikartilan._pay * _payda;
        _pay=_pay * cikartilan._payda;
        cikan._pay=cikartilan._pay - _pay ;
        return cikan;
    }
    else;{
        cikan._pay = _pay - cikartilan._pay;
        cikan._payda = cikartilan._payda;
        return cikan;
    }
    return cikan;
}
Kesirler operator/(const Kesirler &bolunen) {
        Kesirler bolum;
        bolum._pay = _pay * bolunen._payda;
        bolum._payda = _payda * bolunen._pay;
        return bolum;
    }
Kesirler operator*(const Kesirler &carpilan) {
    Kesirler carpim;
    carpim._pay = _pay * carpilan._pay;
    carpim._payda = _payda * carpilan._payda;
    return carpim;
}
Kesirler(const char string[]);
};
std::ostream& operator<<(std::ostream& cikti, const Kesirler &sayi) {
    cikti<< sayi._pay<< "/" << sayi._payda;
    return cikti;
}
std::istream& operator>>(std::istream& girdi, Kesirler& sayi){
    girdi >> sayi._pay >> sayi._payda;
    return girdi;
}
Kesirler::Kesirler(const char *string) {
}
int main(){
    Kesirler b;
    Kesirler a;
    std::cout << "Ilk değer olarak pay ve paydayi sayi cinsinden giriniz.(once pay sonra payda) :" << std::endl;
    std::cin >> a;
    std::cout << "Ikinci pay ve paydayi sayi cinsinden giriniz.(once pay sonra payda) :" << std::endl;
    std::cin >> b;
    std::cout << a << " " << b << std::endl;
    std::cout << "A + B = " << a + b << std::endl;
    std::cout << "A - B = " << a - b << std::endl;
    std::cout << "A * B = " << a * b << std::endl;
    std::cout << "A / B = " << a / b << std::endl;
}

