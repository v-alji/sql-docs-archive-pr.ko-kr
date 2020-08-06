---
title: XML 파일로 정책 기반 관리 패싯 상태 복사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7be2332d9a2507a079d85a3424bda3a387609ca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731519"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a><span data-ttu-id="5fe3c-102">XML 파일로 정책 기반 관리 패싯 상태 복사</span><span class="sxs-lookup"><span data-stu-id="5fe3c-102">Copy a Policy-Based Management Facet State to an XML File</span></span>
  <span data-ttu-id="5fe3c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책 기반 관리 패싯의 상태를 XML 파일에 복사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-103">This topic describes how to how to copy the state of a Policy-Based Management facet to an XML file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5fe3c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5fe3c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5fe3c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5fe3c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5fe3c-106">보안</span><span class="sxs-lookup"><span data-stu-id="5fe3c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5fe3c-107">**다음을 사용하여 패싯 상태를 XML 파일에 복사하려면:**</span><span class="sxs-lookup"><span data-stu-id="5fe3c-107">**To copy a facet state to an XML file, using:**</span></span>  
  
     [<span data-ttu-id="5fe3c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5fe3c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5fe3c-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5fe3c-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5fe3c-110">보안</span><span class="sxs-lookup"><span data-stu-id="5fe3c-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5fe3c-111">권한</span><span class="sxs-lookup"><span data-stu-id="5fe3c-111">Permissions</span></span>  
 <span data-ttu-id="5fe3c-112">이 항목의 절차를 수행하려면 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-112">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5fe3c-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5fe3c-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a><span data-ttu-id="5fe3c-114">패싯 상태를 XML 파일에 복사하려면</span><span class="sxs-lookup"><span data-stu-id="5fe3c-114">To copy a facet state to an XML file</span></span>  
  
1.  <span data-ttu-id="5fe3c-115">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-115">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance object, database, or database object, and then click **Facets**.</span></span>  
  
2.  <span data-ttu-id="5fe3c-116">**패싯 보기-**_object_name_ 대화 상자에서 **정책으로 현재 상태 내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-116">In the **View Facets -**_object_name_ dialog box, click **Export Current State as Policy**.</span></span>  
  
3.  <span data-ttu-id="5fe3c-117">**정책으로 내보내기** 대화 상자에서 파일의 경로와 이름을 입력하거나 찾아보기(**...**) 단추를 사용하여 파일을 찾은 다음 XML 파일의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-117">In the **Export as Policy** dialog box, type the path and name of the file; or use the Browse (**...**) button to locate the file, and then type the name of the XML file.</span></span> <span data-ttu-id="5fe3c-118">이 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [Export As Policy Dialog Box](export-as-policy-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-118">For more information on the available options in this dialog box, see [Export As Policy Dialog Box](export-as-policy-dialog-box.md)</span></span>  
  
4.  <span data-ttu-id="5fe3c-119">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5fe3c-119">When finished, click **OK**.</span></span>  
  
  
