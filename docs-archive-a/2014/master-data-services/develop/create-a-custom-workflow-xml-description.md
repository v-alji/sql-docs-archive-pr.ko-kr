---
title: 사용자 지정 워크플로 XML 설명(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77906426ddb901ec422367bf30aabef2e532ad06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661691"
---
# <a name="custom-workflow-xml-description-master-data-services"></a><span data-ttu-id="74980-102">사용자 지정 워크플로 XML 설명(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="74980-102">Custom Workflow XML Description (Master Data Services)</span></span>
  <span data-ttu-id="74980-103">에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) 는 워크플로가 시작 될 때 MDS 워크플로 통합 서비스를 SQL Server 하 여 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="74980-104">이 메서드는 워크플로 비즈니스 규칙을 트리거한 항목에 대한 메타데이터 및 데이터를 XML 블록으로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="74980-104">This method receives metadata and data about the item that triggered the workflow business rule as a block of XML.</span></span> <span data-ttu-id="74980-105">워크플로 처리기를 구현하는 예제 코드는 [사용자 지정 워크플로 예제&#40;Master Data Services&#41;](create-a-custom-workflow-example.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74980-105">For example code that implements a workflow handler, see [Custom Workflow Example &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).</span></span>  
  
 <span data-ttu-id="74980-106">다음 예제에서는 워크플로 처리기로 전송되는 XML을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="74980-106">The following example shows what the XML that is sent to the workflow handler might look like:</span></span>  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 <span data-ttu-id="74980-107">다음 표에서는 이 XML에 포함되는 태그 일부에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="74980-107">The following table describes some of the tags contained in this XML:</span></span>  
  
|<span data-ttu-id="74980-108">태그</span><span class="sxs-lookup"><span data-stu-id="74980-108">Tag</span></span>|<span data-ttu-id="74980-109">Description</span><span class="sxs-lookup"><span data-stu-id="74980-109">Description</span></span>|  
|---------|-----------------|  
|\<Type>|<span data-ttu-id="74980-110">로드할 사용자 지정 워크플로 어셈블리를 식별하기 위해 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 유형** 입력란에 입력한 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-110">The text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to identify which custom workflow assembly to load.</span></span>|  
|\<SendData>|<span data-ttu-id="74980-111">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **메시지에 멤버 데이터 포함** 확인란으로 제어하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-111">A Boolean value controlled by the **Include member data in the message** checkbox in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="74980-112">값이 1 이면 \<MemberData> 섹션이 전송 되 고, 그렇지 않으면 \<MemberData> 섹션이 전송 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74980-112">A value of 1 means that the \<MemberData> section is sent; otherwise the \<MemberData> section is not sent.</span></span>|  
|<span data-ttu-id="74980-113"><Server_URL></span><span class="sxs-lookup"><span data-stu-id="74980-113"><Server_URL></span></span>|<span data-ttu-id="74980-114">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 사이트** 입력란에 입력한 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-114">The text you entered in the **Workflow site** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|<span data-ttu-id="74980-115"><Action_ID></span><span class="sxs-lookup"><span data-stu-id="74980-115"><Action_ID></span></span>|<span data-ttu-id="74980-116">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 이름** 입력란에 입력한 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-116">The text you entered in the **Workflow name** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|\<MemberData>|<span data-ttu-id="74980-117">워크플로 동작을 트리거한 멤버의 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="74980-117">Contains the data of the member that triggered the workflow action.</span></span> <span data-ttu-id="74980-118">의 값이 1 인 경우에만 포함 됩니다 \<SendData> .</span><span class="sxs-lookup"><span data-stu-id="74980-118">This is included only if the value of \<SendData> is 1.</span></span>|  
|\<Enter*xxx*>|<span data-ttu-id="74980-119">이 태그 집합에는 멤버 생성에 대한 메타데이터(예: 만든 날짜, 만든 사람 등)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74980-119">This set of tags contains metadata about the creation of the member, such as when it was created and who created it.</span></span>|  
|\<LastChg*xxx*>|<span data-ttu-id="74980-120">이 태그 집합에는 멤버에 적용된 마지막 변경 내용에 대한 메타데이터(예: 변경 내용을 적용한 날짜, 변경 내용을 적용한 사람 등)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74980-120">This set of tags contains metadata about the last change made to the member, such as when the change was made and who made it.</span></span>|  
|\<Name>|<span data-ttu-id="74980-121">변경된 멤버의 첫 번째 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-121">The first attribute of the member that was changed.</span></span> <span data-ttu-id="74980-122">이 예제 멤버에는 Name 및 Code 특성만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74980-122">This example member contains only Name and Code attributes.</span></span>|  
|\<Code>|<span data-ttu-id="74980-123">변경된 멤버의 다음 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="74980-123">The next attribute of the member that was changed.</span></span> <span data-ttu-id="74980-124">이 예제 멤버에 더 많은 특성이 포함될 경우 해당 특성은 이 특성 다음에 오게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74980-124">If this example member contained more attributes, they would follow this one.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74980-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74980-125">See Also</span></span>  
 <span data-ttu-id="74980-126">[사용자 지정 워크플로 &#40;MDS(Master Data Services)를 만듭니다&#41;](create-a-custom-workflow-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="74980-126">[Create a Custom Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md) </span></span>  
 [<span data-ttu-id="74980-127">사용자 지정 워크플로 예제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="74980-127">Custom Workflow Example &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-example.md)  
  
  
