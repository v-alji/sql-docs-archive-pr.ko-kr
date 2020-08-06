---
title: DiffGram 예제 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], examples
- examples [SQLXML], DiffGram
- diffgr:parentID
- parentID annotation
ms.assetid: fc148583-dfd3-4efb-a413-f47b150b0975
author: rothja
ms.author: jroth
ms.openlocfilehash: 04fb355af01f9853149a84af72471375d9135468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651597"
---
# <a name="diffgram-examples-sqlxml-40"></a><span data-ttu-id="6dd70-102">DiffGram 예(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6dd70-102">DiffGram Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="6dd70-103">이 항목에서 설명하는 예는 데이터베이스에 대한 삽입, 업데이트 및 삭제 작업을 수행하는 DiffGram으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-103">The examples in this topic consist of DiffGrams that perform insert, update, and delete operations to the database.</span></span> <span data-ttu-id="6dd70-104">예를 사용하기 전에 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6dd70-104">Before using the examples, note the following:</span></span>  
  
-   <span data-ttu-id="6dd70-105">DiffGram 예를 테스트하려면 예에 사용되는 두 개의 테이블(Cust 및 Ord)을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-105">The examples use two tables (Cust and Ord) that must be created if you want to test the DiffGram examples:</span></span>  
  
    ```  
    Cust(CustomerID, CompanyName, ContactName)  
    Ord(OrderID, CustomerID)  
    ```  
  
-   <span data-ttu-id="6dd70-106">이 항목의 예 중 대부분에는 다음 XSD 스키마가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-106">Most of the examples in this topic use the following XSD Schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
    <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
    <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
    </xsd:element>  
  
    </xsd:schema>     
    ```  
  
     <span data-ttu-id="6dd70-107">이 스키마를 예에 사용되는 다른 파일을 저장한 폴더와 같은 폴더에 DiffGramSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-107">Save this schema as DiffGramSchema.xml in the same folder where you save other files used in the examples.</span></span>  
  
## <a name="a-deleting-a-record-by-using-a-diffgram"></a><span data-ttu-id="6dd70-108">A.</span><span class="sxs-lookup"><span data-stu-id="6dd70-108">A.</span></span> <span data-ttu-id="6dd70-109">DiffGram을 사용하여 레코드 삭제</span><span class="sxs-lookup"><span data-stu-id="6dd70-109">Deleting a record by using a DiffGram</span></span>  
 <span data-ttu-id="6dd70-110">이 예의 DiffGram은 Cust 테이블에서 CustomerID가 ALFKI인 고객 레코드를 삭제하고 Ord 테이블에서 OrderID가 1인 해당 주문 레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-110">The DiffGram in this example deletes a customer (whose CustomerID is ALFKI) record from the Cust table and deletes the corresponding order record (whose OrderID is 1) from the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance/>  
  
    <diffgr:before>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI"   
               OrderID="1"/>  
        <Customer diffgr:id="Customer1"   
                  msdata:rowOrder="0"   
                  CustomerID="ALFKI">  
           <CompanyName>Alfreds Futterkiste</CompanyName>  
           <ContactName>Maria Anders</ContactName>  
        </Customer>  
    </diffgr:before>  
    <msdata:errors/>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="6dd70-111">블록에 **\<before>** 는 **\<Order>** 요소 (**diffgr: Id = "Order1"**)와 **\<Customer>** 요소 (**Diffgr: id = "Customer1"**)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-111">In the **\<before>** block, there is an **\<Order>** element (**diffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="6dd70-112">이러한 요소는 데이터베이스의 기존 레코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-112">These elements represent existing records in the database.</span></span> <span data-ttu-id="6dd70-113">요소에 해당 하는 **\<DataInstance>** 레코드 ( **diffgr: id**가 같음)가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-113">The **\<DataInstance>** element does not have the corresponding records (with the same **diffgr:id**).</span></span> <span data-ttu-id="6dd70-114">이는 삭제 작업임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-114">This indicates a delete operation.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="6dd70-115">DiffGram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6dd70-115">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="6dd70-116">이러한 테이블을 **tempdb** 데이터베이스에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-116">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="6dd70-117">다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-117">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="6dd70-118">위 DiffGram을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-118">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="6dd70-119">파일을 이전 단계에 사용된 폴더와 같은 폴더에 MyDiffGram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-119">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="6dd70-120">이 항목의 앞에서 제공된 DiffGramSchema를 복사하여 텍스트 파일로 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-120">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="6dd70-121">파일을 DiffGramSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-121">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="6dd70-122">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-122">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="6dd70-123">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6dd70-123">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="b-inserting-a-record-by-using-a-diffgram"></a><span data-ttu-id="6dd70-124">B.</span><span class="sxs-lookup"><span data-stu-id="6dd70-124">B.</span></span> <span data-ttu-id="6dd70-125">DiffGram을 사용하여 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="6dd70-125">Inserting a record by using a DiffGram</span></span>  
 <span data-ttu-id="6dd70-126">이 예에서 DiffGram은 Cust 테이블과 Ord 테이블에 레코드를 하나씩 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-126">In this example, the DiffGram inserts a record in the Cust table and a record in the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"   
      sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
          xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
          xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
       <Customer diffgr:id="Customer1" msdata:rowOrder="0"    
                 diffgr:hasChanges="inserted" CustomerID="ALFKI">  
        <CompanyName>C3Company</CompanyName>  
        <ContactName>C3Contact</ContactName>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"  
               diffgr:hasChanges="inserted"   
               CustomerID="ALFKI" OrderID="1"/>  
      </Customer>  
    </DataInstance>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="6dd70-127">이 DiffGram에서 **\<before>** 블록이 지정 되지 않았습니다 (기존 데이터베이스 레코드를 식별 하지 않음).</span><span class="sxs-lookup"><span data-stu-id="6dd70-127">In this DiffGram the **\<before>** block is not specified (no existing database records identified).</span></span> <span data-ttu-id="6dd70-128">**\<Customer>** **\<Order>** **\<DataInstance>** 각각 Cust 및 Ord 테이블에 매핑되는 두 개의 레코드 인스턴스 (블록의 및 요소로 식별 됨)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-128">There are two record instances (identified by the **\<Customer>** and **\<Order>** elements in the **\<DataInstance>** block) that map to Cust and Ord tables, respectively.</span></span> <span data-ttu-id="6dd70-129">이러한 두 요소는 모두 **diffgr: haschanges** 특성을 지정 합니다 (**haschanges = "inserted"**).</span><span class="sxs-lookup"><span data-stu-id="6dd70-129">Both of these elements specify the **diffgr:hasChanges** attribute (**hasChanges="inserted"**).</span></span> <span data-ttu-id="6dd70-130">이는 삽입 작업임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-130">This indicates an insert operation.</span></span> <span data-ttu-id="6dd70-131">이 DiffGram에서 **Haschanges = "modified"** 를 지정 하는 경우 존재 하지 않는 레코드를 수정 하 고 오류가 발생 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-131">In this DiffGram, if you specify **hasChanges="modified"**, you are indicating that you want to modify a record that does not exist, which results in an error.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="6dd70-132">DiffGram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6dd70-132">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="6dd70-133">이러한 테이블을 **tempdb** 데이터베이스에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-133">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="6dd70-134">다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-134">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="6dd70-135">위 DiffGram을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-135">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="6dd70-136">파일을 이전 단계에 사용된 폴더와 같은 폴더에 MyDiffGram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-136">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="6dd70-137">이 항목의 앞에서 제공된 DiffGramSchema를 복사하여 텍스트 파일로 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-137">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="6dd70-138">파일을 DiffGramSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-138">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="6dd70-139">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-139">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="6dd70-140">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6dd70-140">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="c-updating-an-existing-record-by-using-a-diffgram"></a><span data-ttu-id="6dd70-141">C.</span><span class="sxs-lookup"><span data-stu-id="6dd70-141">C.</span></span> <span data-ttu-id="6dd70-142">DiffGram을 사용하여 기존 레코드 업데이트</span><span class="sxs-lookup"><span data-stu-id="6dd70-142">Updating an existing record by using a DiffGram</span></span>  
 <span data-ttu-id="6dd70-143">이 예에서 DiffGram은 고객 ALFKI의 고객 정보(CompanyName 및 ContactName)를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-143">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="6dd70-144">**\<before>** 블록에는 **\<Customer>** 요소 (**diffgr: Id = "Customer1"**)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-144">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="6dd70-145">블록에는 **\<DataInstance>** **\<Customer>** **id가**같은 해당 요소가 포함 됩니다. **\<customer>** 의 요소는 **\<NewDataSet>** **Diffgr: haschanges = "modified"** 도 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-145">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="6dd70-146">이는 업데이트 작업을 나타내며,이에 따라 **Cust** 테이블의 고객 레코드가 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-146">This indicates an update operation, and the customer record in the **Cust** table is updated accordingly.</span></span> <span data-ttu-id="6dd70-147">**Diffgr: hasChanges** 특성이 지정 되지 않은 경우 DiffGram 처리 논리는이 요소를 무시 하 고 업데이트를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-147">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="6dd70-148">DiffGram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6dd70-148">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="6dd70-149">이러한 테이블을 **tempdb** 데이터베이스에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-149">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="6dd70-150">다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-150">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="6dd70-151">위 DiffGram을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-151">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="6dd70-152">파일을 이전 단계에 사용된 폴더와 같은 폴더에 MyDiffGram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-152">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="6dd70-153">이 항목의 앞에서 제공된 DiffGramSchema를 복사하여 텍스트 파일로 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-153">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="6dd70-154">파일을 DiffGramSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-154">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="6dd70-155">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-155">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="6dd70-156">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6dd70-156">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="d-inserting-updating-and-deleting-records-by-using-a-diffgram"></a><span data-ttu-id="6dd70-157">D.</span><span class="sxs-lookup"><span data-stu-id="6dd70-157">D.</span></span> <span data-ttu-id="6dd70-158">DiffGram을 사용하여 레코드 삽입, 업데이트 및 삭제</span><span class="sxs-lookup"><span data-stu-id="6dd70-158">Inserting, updating, and deleting records by using a DiffGram</span></span>  
 <span data-ttu-id="6dd70-159">이 예에서는 비교적 복잡한 DiffGram을 사용하여 삽입, 업데이트 및 삭제 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-159">In this example, a relatively complex DiffGram is used to perform insert, update, and delete operations.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                diffgr:hasChanges="modified"   
                CustomerID="ANATR">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Elizabeth Lincoln</ContactName>  
          <Order diffgr:id="Order2" msdata:rowOrder="1"   
               msdata:hiddenCustomerID="ANATR"   
               CustomerID="ANATR" OrderID="2"/>  
      </Customer>  
  
      <Customer diffgr:id="Customer3" msdata:rowOrder="2"   
                CustomerID="ANTON">  
         <CompanyName>Chop-suey Chinese</CompanyName>  
         <ContactName>Yang Wang</ContactName>  
         <Order diffgr:id="Order3" msdata:rowOrder="2"   
               msdata:hiddenCustomerID="ANTON"   
               CustomerID="ANTON" OrderID="3"/>  
      </Customer>  
      <Customer diffgr:id="Customer4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                CustomerID="AROUT">  
         <CompanyName>Around the Horn</CompanyName>  
         <ContactName>Thomas Hardy</ContactName>  
         <Order diffgr:id="Order4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                msdata:hiddenCustomerID="AROUT"   
               CustomerID="AROUT" OrderID="4"/>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
      <Order diffgr:id="Order1" msdata:rowOrder="0"   
             msdata:hiddenCustomerID="ALFKI"   
             CustomerID="ALFKI" OrderID="1"/>  
      <Customer diffgr:id="Customer1" msdata:rowOrder="0"   
                CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                CustomerID="ANATR">  
        <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
        <ContactName>Ana Trujillo</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="6dd70-160">DiffGram 논리는 이 DiffGram을 다음과 같이 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-160">The DiffGram logic processes this DiffGram as follows:</span></span>  
  
-   <span data-ttu-id="6dd70-161">DiffGram 처리 논리에 따라 블록의 모든 최상위 요소는 **\<before>** 매핑 스키마에 설명 된 대로 해당 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-161">In accordance with DiffGram processing logic, all the top-level elements in the **\<before>** block map to corresponding tables, as described in the mapping schema.</span></span>  
  
-   <span data-ttu-id="6dd70-162">블록에는 **\<before>** **\<Order>** 요소 (**dffgr: Id = "Order1"**)와 요소 **\<Customer>** (**Diffgr: id = "Customer1"**)가 있습니다 .이 요소에는 블록에 해당 하는 요소가 없습니다 **\<DataInstance>** (id는 동일 함).</span><span class="sxs-lookup"><span data-stu-id="6dd70-162">The **\<before>** block has an **\<Order>** element (**dffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**) for which there is no corresponding element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="6dd70-163">이는 삭제 작업임을 나타내며 Cust 테이블과 Ord 테이블에서 레코드가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-163">This indicates a delete operation, and the records are deleted from the Cust and Ord tables.</span></span>  
  
-   <span data-ttu-id="6dd70-164">블록 **\<before>** **\<Customer>** 에는 동일한 id를 가진 블록에 해당 요소가 있는 요소 (**diffgr: Id = "Customer2"**)가 있습니다 **\<Customer>** **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="6dd70-164">The **\<before>** block has a **\<Customer>** element (**diffgr:id="Customer2"**) for which there is a corresponding **\<Customer>** element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="6dd70-165">블록의 요소는 **\<DataInstance>** **diffgr: haschanges = "modified"** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-165">The element in the **\<DataInstance>** block specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="6dd70-166">이 업데이트 작업은 고객 ANATR에 게 블록에 지정 된 값을 사용 하 여 Cust 테이블에서 CompanyName 및 ContactName 정보가 업데이트 되는 업데이트 작업입니다 **\<DataInstance>** .</span><span class="sxs-lookup"><span data-stu-id="6dd70-166">This is an update operation in which for customer ANATR, the CompanyName and ContactName information is updated in the Cust table using values that are specified in the **\<DataInstance>** block.</span></span>  
  
-   <span data-ttu-id="6dd70-167">블록에는 **\<DataInstance>** **\<Customer>** 요소 (**diffgr: Id = "예제의 customer3"**)와 **\<Order>** 요소 (**Diffgr: id = "Order3"**)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-167">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer3"**) and an **\<Order>** element (**diffgr:id="Order3"**).</span></span> <span data-ttu-id="6dd70-168">이러한 요소는 모두 **diffgr: hasChanges** 특성을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-168">Neither of these elements specify the **diffgr:hasChanges** attribute.</span></span> <span data-ttu-id="6dd70-169">따라서 DiffGram 처리 논리에서 이러한 요소는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-169">Therefore, the DiffGram processing logic ignores these elements.</span></span>  
  
-   <span data-ttu-id="6dd70-170">블록 **\<DataInstance>** **\<Customer>** 에는 요소 (**diffgr: Id = "Customer4"**)와 **\<Order>** 블록에 해당 요소가 없는 요소 (**Diffgr: id = "Order4"**)가 있습니다 \<before> .</span><span class="sxs-lookup"><span data-stu-id="6dd70-170">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer4"**) and an **\<Order>** element (**diffgr:id="Order4"**) for which there are no corresponding elements in the \<before> block.</span></span> <span data-ttu-id="6dd70-171">블록의 이러한 요소는 **\<DataInstance>** **diffgr: haschanges = "inserted"** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-171">These elements in the **\<DataInstance>** block specify **diffgr:hasChanges="inserted"**.</span></span> <span data-ttu-id="6dd70-172">따라서 Cust 테이블과 Ord 테이블에 새 레코드가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-172">Therefore, a new record is added in the Cust table and in the Ord table.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="6dd70-173">DiffGram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6dd70-173">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="6dd70-174">**Tempdb** 데이터베이스에 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-174">Create the following tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="6dd70-175">다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-175">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="6dd70-176">위 DiffGram을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-176">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="6dd70-177">파일을 이전 단계에 사용된 폴더와 같은 폴더에 MyDiffGram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-177">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="6dd70-178">이 항목의 앞에서 제공된 DiffGramSchema를 복사하여 텍스트 파일로 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-178">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="6dd70-179">파일을 DiffGramSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-179">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="6dd70-180">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-180">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="6dd70-181">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6dd70-181">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="e-applying-updates-by-using-a-diffgram-with-the-diffgrparentid-annotation"></a><span data-ttu-id="6dd70-182">E.</span><span class="sxs-lookup"><span data-stu-id="6dd70-182">E.</span></span> <span data-ttu-id="6dd70-183">diffgr:parentID 주석이 지정된 DiffGram을 사용하여 업데이트 적용</span><span class="sxs-lookup"><span data-stu-id="6dd70-183">Applying updates by using a DiffGram with the diffgr:parentID annotation</span></span>  
 <span data-ttu-id="6dd70-184">이 예에서는 DiffGram의 블록에 지정 된 **parentID** 주석을 **\<before>** 업데이트를 적용 하는 데 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-184">This example illustrates how the **parentID** annotation that is specified in the **\<before>** block of the DiffGram is used in applying the updates.</span></span>  
  
```  
<NewDataSet />  
<diffgr:before>  
   <Order diffgr:id="Order1" msdata:rowOrder="0" OrderID="2" />  
   <Order diffgr:id="Order3" msdata:rowOrder="2" OrderID="4" />  
  
   <OrderDetail diffgr:id="OrderDetail1"   
                diffgr:parentId="Order1"   
                msdata:rowOrder="0"   
                ProductID="13"   
                OrderID="2" />  
   <OrderDetail diffgr:id="OrderDetail3"   
                diffgr:parentId="Order3"  
                ProductID="77"  
                OrderID="4"/>  
</diffgr:before>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="6dd70-185">이 DiffGram은 블록만 있으므로 삭제 작업을 지정 합니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="6dd70-185">This DiffGram specifies a delete operation because there is only a **\<before>** block.</span></span> <span data-ttu-id="6dd70-186">DiffGram에서 **parentID** 주석은 주문 및 주문 세부 정보 간에 부모-자식 관계를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-186">In the DiffGram, the **parentID** annotation is used to specify a parent-child relationship between the orders and order details.</span></span> <span data-ttu-id="6dd70-187">SQLXML에서 레코드를 삭제할 때 이 관계를 통해 식별된 자식 테이블에서 레코드가 삭제되고 해당 부모 테이블에서도 레코드가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="6dd70-187">When SQLXML deletes the records, it deletes records from the child table that is identified by this relationship and then deletes the records from the corresponding parent table.</span></span>  
  
  
