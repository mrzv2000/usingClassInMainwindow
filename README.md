
//mainWindow be like:
# usingClassInMainwindow
#include "mainwindow.h"
#include "ui_mainwindow.h"
#include "testingshowsomething.h"
#include<QMessageBox>
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
    , ui(new Ui::MainWindow)
{
    ui->setupUi(this);
}

MainWindow::~MainWindow()
{
    delete ui;
}


void MainWindow::on_show_clicked()
{
    testingShowSomething obj1;
    int age = obj1.calculateAge(ui->yearLine->text());
    QString message = "Your age is " + QString::number(age);
    QMessageBox::information(this , tr("Announcing Age") , (message));
}
//testing.cpp be like:
#include "testingshowsomething.h"
#include<QString>
testingShowSomething::testingShowSomething()
{

}


int testingShowSomething::calculateAge(QString yearOfBirth){
    int age = 2023-yearOfBirth.toInt();
    return age;
}
//mainwindow.h be like:
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <QMainWindow>

QT_BEGIN_NAMESPACE
namespace Ui { class MainWindow; }
QT_END_NAMESPACE

class MainWindow : public QMainWindow
{
    Q_OBJECT

public:
    MainWindow(QWidget *parent = nullptr);
    ~MainWindow();

private slots:
    void on_show_clicked();

private:
    Ui::MainWindow *ui;
};
#endif // MAINWINDOW_H
//testing.h be like:
#ifndef TESTINGSHOWSOMETHING_H
#define TESTINGSHOWSOMETHING_H
#include<QString>
using namespace std;

class testingShowSomething
{
private:
    QString yearOfBirth;
    int age;
public:
    testingShowSomething();
    int calculateAge(QString);
};

#endif // TESTINGSHOWSOMETHING_H
