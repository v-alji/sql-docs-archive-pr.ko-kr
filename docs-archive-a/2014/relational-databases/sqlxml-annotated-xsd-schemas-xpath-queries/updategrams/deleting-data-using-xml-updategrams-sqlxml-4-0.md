---
title: XML Updategrams을 사용 하 여 데이터 삭제 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: rothja
ms.author: jroth
ms.openlocfilehash: d941005c71dc33dd8c4f5c5cc15f645cd0e68177
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653767"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a><span data-ttu-id="888db-102">XML Updategram을 사용하여 데이터 삭제(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="888db-102">Deleting Data Using XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="888db-103">Updategram는 레코드 인스턴스가 블록에 **\<before>** 해당 레코드가 없는 블록에 표시 되는 경우 삭제 작업을 나타냅니다 **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="888db-103">An updategram indicates a delete operation when a record instance appears in the **\<before>** block with no corresponding records in the **\<after>** block.</span></span> <span data-ttu-id="888db-104">이 경우 updategram는 데이터베이스에서 블록의 레코드를 삭제 합니다 **\<before>** .</span><span class="sxs-lookup"><span data-stu-id="888db-104">In this case, the updategram deletes the record in the **\<before>** block from the database.</span></span>  
  
 <span data-ttu-id="888db-105">삭제 작업에 대한 Updategram 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="888db-105">This is the updategram format for a delete operation:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 <span data-ttu-id="888db-106">**\<after>** Updategram가 삭제 작업만 수행 하는 경우 태그를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="888db-106">You can omit the **\<after>** tag if the updategram is performing only a delete operation.</span></span> <span data-ttu-id="888db-107">선택적 특성을 지정 하지 않으면 `mapping-schema` **\<ElementName>** updategram에 지정 된가 데이터베이스 테이블에 매핑되고 자식 요소 또는 특성은 테이블의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="888db-107">If you do not specify the optional `mapping-schema` attribute, the **\<ElementName>** specified in the updategram maps to a database table and the child elements or attributes map to columns in the table.</span></span>  
  
 <span data-ttu-id="888db-108">Updategram에 지정 된 요소가 테이블에서 둘 이상의 행과 일치 하거나 행과 일치 하지 않는 경우 updategram는 오류를 반환 하 고 전체 블록을 취소 합니다 **\<sync>** .</span><span class="sxs-lookup"><span data-stu-id="888db-108">If an element specified in the updategram either matches more than one row in the table or does not match any row, the updategram returns an error and cancels the entire **\<sync>** block.</span></span> <span data-ttu-id="888db-109">Updategram의 요소는 한 번에 하나의 레코드만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="888db-109">Only one record at a time can be deleted by an element in the updategram.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="888db-110">예</span><span class="sxs-lookup"><span data-stu-id="888db-110">Examples</span></span>  
 <span data-ttu-id="888db-111">이 섹션의 예에서는 기본 매핑을 사용합니다. 즉, Updategram에 매핑 스키마가 지정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="888db-111">Examples in this section use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="888db-112">매핑 스키마를 사용 하는 updategram의 추가 예제는 [Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정 ](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="888db-112">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="888db-113">다음 예제를 사용 하 여 작업 예제를 만들려면 [SQLXML 예를 실행 하기 위한 요구 사항](../../sqlxml/requirements-for-running-sqlxml-examples.md)에 지정 된 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-113">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a><span data-ttu-id="888db-114">A.</span><span class="sxs-lookup"><span data-stu-id="888db-114">A.</span></span> <span data-ttu-id="888db-115">Updategram을 사용하여 단일 레코드 삭제</span><span class="sxs-lookup"><span data-stu-id="888db-115">Deleting a record by using an updategram</span></span>  
 <span data-ttu-id="888db-116">다음 Updategram은 HumanResources.Shift 테이블에서 레코드 두 개를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-116">The following updategrams deletes two records from the HumanResources.Shift table.</span></span>  
  
 <span data-ttu-id="888db-117">이러한 예에서 Updategram은 매핑 스키마를 지정하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="888db-117">In these examples, the updategram does not specify a mapping schema.</span></span> <span data-ttu-id="888db-118">요소 이름은 테이블 이름에 매핑되고 특성 또는 하위 요소는 열에 매핑되는 기본 매핑을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-118">Therefore, the updategram uses default mapping, in which the element name maps to table name and the attributes or subelements map to columns.</span></span>  
  
 <span data-ttu-id="888db-119">이 첫 번째 updategram는 특성 중심 이며 블록에서 두 교대 교대 (야간 및 야간 시간)을 식별 **\<before>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-119">This first updategram is attribute-centric and identifies two shifts (Day-Evening and Evening-Night) in the **\<before>** block.</span></span> <span data-ttu-id="888db-120">블록에 해당 레코드가 없기 때문에 **\<after>** 이는 삭제 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="888db-120">Because there is no corresponding record in the **\<after>** block, this is a delete operation.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="888db-121">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="888db-121">To test the updategram</span></span>  
  
1.  <span data-ttu-id="888db-122">[XML Updategrams &#40;SQLXML 4.0&#41;를 사용 하 여 데이터 삽입 ](inserting-data-using-xml-updategrams-sqlxml-4-0.md)에서 예제 B ("updategram를 사용 하 여 여러 레코드 삽입")를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-122">Complete example B ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="888db-123">위의 updategram을 메모장에 복사 하 고 [XML Updategrams &#40;SQLXML 4.0&#41;를 사용 하 여 데이터 삽입 ](inserting-data-using-xml-updategrams-sqlxml-4-0.md)에서 완료 하는 데 사용한 것과 동일한 폴더 ("updategram를 사용 하 여 여러 레코드 삽입")에 Updategram-RemoveShifts.xml로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-123">Copy the updategram above to Notepad and save it as Updategram-RemoveShifts.xml in the same folder as was used to complete ("Inserting multiple records by using an updategram") in [Inserting Data Using XML Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).</span></span>  
  
3.  <span data-ttu-id="888db-124">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 Updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="888db-124">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the updategram.</span></span>  
  
     <span data-ttu-id="888db-125">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="888db-125">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888db-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="888db-126">See Also</span></span>  
 [<span data-ttu-id="888db-127">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="888db-127">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
