---
title: Updategrams의 데이터베이스 동시성 문제 처리 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: rothja
ms.author: jroth
ms.openlocfilehash: dd808b2688e8bf05149a5454bee91123878fb2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652743"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a><span data-ttu-id="940b6-102">Updategram의 데이터베이스 동시성 문제 처리(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="940b6-102">Handling Database Concurrency Issues in Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="940b6-103">다른 데이터베이스 업데이트 메커니즘과 마찬가지로 updategram에서도 다중 사용자 환경에서 데이터의 동시 업데이트를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-103">Like other database update mechanisms, updategrams must deal with concurrent updates to data in a multiuser environment.</span></span> <span data-ttu-id="940b6-104">Updategram은 선택한 필드 데이터의 스냅샷을 비교하는 방법으로 업데이트 대상 데이터를 데이터베이스에서 마지막으로 읽은 이후 다른 사용자 애플리케이션에서 해당 데이터를 변경했는지 여부를 확인하는 낙관적 동시성 제어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-104">Updategrams use the Optimistic Concurrency Control, which uses comparison of select field data as snapshots to ensure that the data to be updated has not been altered by another user application since it was read from the database.</span></span> <span data-ttu-id="940b6-105">Updategrams은 updategrams 블록에 이러한 스냅숏 값을 포함 **\<before>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-105">Updategrams include these snapshot values in the **\<before>** block of the updategrams.</span></span> <span data-ttu-id="940b6-106">데이터베이스를 업데이트 하기 전에 updategram은 블록에 지정 된 값을 **\<before>** 데이터베이스에 현재 있는 값과 비교 하 여 업데이트가 유효한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-106">Before updating the database, the updategram checks the values that are specified in the **\<before>** block against the values currently in the database to ensure that the update is valid.</span></span>  
  
 <span data-ttu-id="940b6-107">낙관적 동시성 제어는 updategram에 낮음(없음), 중간, 높음이라는 세 가지 보호 수준을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-107">The Optimistic Concurrency Control offers three levels of protection in an updategram: low (none), intermediate, and high.</span></span> <span data-ttu-id="940b6-108">Updategram을 적절하게 지정하여 필요한 보호 수준을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-108">You can decide what level of protection you need by specifying the updategram accordingly.</span></span>  
  
## <a name="lowest-level-of-protection"></a><span data-ttu-id="940b6-109">가장 낮은 수준의 보호</span><span class="sxs-lookup"><span data-stu-id="940b6-109">Lowest Level of Protection</span></span>  
 <span data-ttu-id="940b6-110">이 보호 수준에서는 데이터베이스를 마지막으로 읽은 후 적용된 다른 업데이트에 대한 참조 없이 업데이트가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-110">This level is a blind update, in which the update is processed without reference to other updates that have been made since the database was last read.</span></span> <span data-ttu-id="940b6-111">이 경우 블록에서 레코드를 식별 하는 기본 키 열만 지정 하 **\<before>** 고 블록에 업데이트 된 정보를 지정 합니다 **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="940b6-111">In such a case, you specify only the primary key column(s) in the **\<before>** block to identify the record, and you specify the updated information in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="940b6-112">예를 들어 다음 updategram에서 새 연락처 전화 번호는 이전 전화 번호가 무엇이었는지에 상관없이 올바른 전화 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-112">For example, the new contact phone number in the following updategram is correct, regardless of what the phone number was previously.</span></span> <span data-ttu-id="940b6-113">**\<before>** 블록에서 기본 키 열 (ContactID)만 지정 하는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-113">Notice how the **\<before>** block specifies only the primary key column (ContactID).</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a><span data-ttu-id="940b6-114">중간 수준의 보호</span><span class="sxs-lookup"><span data-stu-id="940b6-114">Intermediate Level of Protection</span></span>  
 <span data-ttu-id="940b6-115">이 보호 수준의 경우 updategram은 사용자의 트랜잭션에서 레코드를 읽은 후 다른 트랜잭션에서 값을 변경하지 않았는지 확인하기 위해 업데이트 대상 데이터의 현재 값을 데이터베이스 열의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-115">In this level of protection, the updategram compares the current value(s) of the data being updated with the value(s) in the database column(s) to ensure that the values have not been changed by some other transaction since the record was read by your transaction.</span></span>  
  
 <span data-ttu-id="940b6-116">블록에서 업데이트할 기본 키 열과 열을 지정 하 여이 수준의 보호를 가져올 수 있습니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="940b6-116">You can get this level of protection by specifying the primary key column(s) and the column(s) that you are updating in the **\<before>** block.</span></span>  
  
 <span data-ttu-id="940b6-117">예를 들어 다음 updategram은 ContactID가 1인 연락처의 Person.Contact 테이블의 Phone 열 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-117">For example, this updategram changes the value in the Phone column of the Person.Contact table for the contact with ContactID of 1.</span></span> <span data-ttu-id="940b6-118">**\<before>** 블록은 업데이트 된 값을 적용 하기 전에이 특성 값이 데이터베이스의 해당 열에 있는 값과 일치 하는지 확인 하기 위해 **Phone** 특성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-118">The **\<before>** block specifies the **Phone** attribute to ensure that this attribute value matches the value in the corresponding column in the database before applying the updated value.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a><span data-ttu-id="940b6-119">높은 수준의 보호</span><span class="sxs-lookup"><span data-stu-id="940b6-119">High Level of Protection</span></span>  
 <span data-ttu-id="940b6-120">높은 수준의 보호를 사용하면 애플리케이션에서 레코드를 마지막으로 읽은 후 레코드가 동일하게 유지되는지 확인할 수 있습니다. 다시 말해 애플리케이션에서 레코드를 읽은 후 다른 트랜잭션에 의해 해당 레코드가 변경되지 않았다는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-120">A high level of protection ensures that the record remains the same since your application last read that record (that is, since your application has read the record, it has not been changed by any other transaction).</span></span>  
  
 <span data-ttu-id="940b6-121">다음과 같은 두 가지 방법으로 동시 업데이트에 대해 이와 같은 높은 수준의 보호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-121">There are two ways you can get this high level of protection against concurrent updates:</span></span>  
  
-   <span data-ttu-id="940b6-122">블록의 테이블에서 추가 열을 지정 **\<before>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-122">Specify additional columns in the table in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="940b6-123">블록에서 추가 열을 지정 하 **\<before>** 는 경우 updategram은 이러한 열에 대해 지정 된 값을 업데이트를 적용 하기 전에 데이터베이스에 있는 값과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-123">If you specify additional columns in the **\<before>** block, the updategram compares the values that are specified for these columns with the values that were in the database before applying the update.</span></span> <span data-ttu-id="940b6-124">트랜잭션에서 레코드를 읽은 후 레코드 열 중 하나라도 변경되었으면 updategram은 업데이트를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-124">If any of the record columns has changed since your transaction read the record, the updategram does not perform the update.</span></span>  
  
     <span data-ttu-id="940b6-125">예를 들어 다음 updategram은 이동 이름을 업데이트 하지만 블록에 추가 열 (StartTime, EndTime)을 지정 **\<before>** 하 여 동시 업데이트에 대 한 더 높은 수준의 보호를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-125">For example, the following updategram updates the shift name, but specifies additional columns (StartTime,EndTime) in the **\<before>** block, thereby requesting a higher level of protection against concurrent updates.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="940b6-126">이 예에서는 블록의 레코드에 대해 모든 열 값을 지정 하 여 가장 높은 수준의 보호를 지정 합니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="940b6-126">This example specifies the highest level of protection by specifying all column values for the record in the **\<before>** block.</span></span>  
  
-   <span data-ttu-id="940b6-127">블록에서 타임 스탬프 열 (사용 가능한 경우)을 지정 **\<before>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-127">Specify the timestamp column (if available) in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="940b6-128">> 블록의 모든 레코드 열을 지정 하는 대신 `<before` 블록의 기본 키 열과 함께 timestamp 열 (테이블이 있는 경우)을 지정할 수 있습니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="940b6-128">Instead of specifying all the record columns in the `<before`> block, you can just specify the timestamp column (if the table has one) along with the primary key column(s) in the **\<before>** block.</span></span> <span data-ttu-id="940b6-129">데이터베이스는 레코드가 업데이트될 때마다 타임스탬프 열을 고유한 값으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-129">The database updates the timestamp column to a unique value after each update of the record.</span></span> <span data-ttu-id="940b6-130">이 경우 updategram은 타임스탬프 값을 데이터베이스의 해당 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-130">In this case, the updategram compares the value of the timestamp with the corresponding value in the database.</span></span> <span data-ttu-id="940b6-131">타임스탬프 값은 데이터베이스에 이진 값으로 저장되므로</span><span class="sxs-lookup"><span data-stu-id="940b6-131">The timestamp value stored in the database is a binary value.</span></span> <span data-ttu-id="940b6-132">스키마에서 타임스탬프 열은 `dt:type="bin.hex"`, `dt:type="bin.base64"` 또는 `sql:datatype="timestamp"`로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-132">Therefore, the timestamp column must be specified in the schema as `dt:type="bin.hex"`, `dt:type="bin.base64"`, or `sql:datatype="timestamp"`.</span></span> <span data-ttu-id="940b6-133">`xml`데이터 형식 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 데이터 형식 중 하나를 지정할 수 있습니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="940b6-133">(You can specify either the `xml` data type or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.)</span></span>  
  
#### <a name="to-test-the-updategram"></a><span data-ttu-id="940b6-134">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="940b6-134">To test the updategram</span></span>  
  
1.  <span data-ttu-id="940b6-135">**Tempdb** 데이터베이스에이 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-135">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  <span data-ttu-id="940b6-136">이 예제 레코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-136">Add this sample record:</span></span>  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  <span data-ttu-id="940b6-137">다음 XSD 스키마를 복사하여 메모장에 붙여넣고</span><span class="sxs-lookup"><span data-stu-id="940b6-137">Copy the following XSD schema and paste it into Notepad.</span></span> <span data-ttu-id="940b6-138">ConcurrencySampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-138">Save it as ConcurrencySampleSchema.xml:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  <span data-ttu-id="940b6-139">다음 updategram 코드를 메모장에 복사한 다음 이전 단계에서 만든 스키마를 저장한 것과 같은 디렉터리에 ConcurrencySampleTemplate.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-139">Copy the following updategram code into Notepad and save it as ConcurrencySampleTemplate.xml in the same directory where you saved the schema created in the previous step.</span></span> <span data-ttu-id="940b6-140">아래의 LastUpdated 타임스탬프 값은 Customer 테이블의 타임스탬프 값과 다르므로 테이블에서 LastUpdated의 실제 값을 복사하여 updategram에 붙여넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-140">(Note the timestamp value below for LastUpdated will differ in your example Customer table, so copy the actual value for LastUpdated from the table and paste it into the updategram.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="940b6-141">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-141">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="940b6-142">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="940b6-142">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="940b6-143">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="940b6-143">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="940b6-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="940b6-144">See Also</span></span>  
 [<span data-ttu-id="940b6-145">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="940b6-145">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
