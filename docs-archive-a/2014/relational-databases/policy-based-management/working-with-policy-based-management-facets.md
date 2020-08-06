---
title: 정책 기반 관리 패싯 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5a356550796cc682b2292defffd6565b7fea0783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648971"
---
# <a name="working-with-policy-based-management-facets"></a><span data-ttu-id="440f3-102">정책 기반 관리 패싯 작업</span><span class="sxs-lookup"><span data-stu-id="440f3-102">Working with Policy-Based Management Facets</span></span>
  <span data-ttu-id="440f3-103">정책 기반 관리 패싯은 관리하려는 영역과 관련된 논리적 속성 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-103">A Policy-Based Management facet is a set of logical properties that are related to an area of management interest.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="440f3-104">에는 여러 가지의 미리 정의된 패싯이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-104">includes several predefined facets.</span></span> <span data-ttu-id="440f3-105">예를 들어 기본적으로 해제되는 기능을 속성으로 정의하는 노출 영역 구성 패싯이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-105">For example, the Surface Area Configuration facet defines, as properties, the features that are off by default.</span></span>  
  
 <span data-ttu-id="440f3-106">유사한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경을 여러 개 관리하는 경우 하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 패싯을 구성하고 패싯 상태를 파일에 복사한 다음 해당 파일을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 정책으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-106">When you manage many similar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environments, you can configure a facet in one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copy the state of the facet to a file, and then import that file into another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a policy.</span></span> <span data-ttu-id="440f3-107">상태가 정책으로 변환되면 정책을 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-107">When the state has been converted to a policy, the policy can be applied to other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], instance objects, databases, or database objects.</span></span>  
  
 <span data-ttu-id="440f3-108">이 항목에서는 패싯 상태를 XML 파일에 복사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-108">This topic describes how to copy the state of a facet to an XML file.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="440f3-109">권한</span><span class="sxs-lookup"><span data-stu-id="440f3-109">Permissions</span></span>  
 <span data-ttu-id="440f3-110">이 항목의 절차를 수행하려면 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="440f3-110">The procedures in this topic require membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
## <a name="viewing-and-copying-facet-states"></a><span data-ttu-id="440f3-111">패싯 상태 보기 및 복사</span><span class="sxs-lookup"><span data-stu-id="440f3-111">Viewing and Copying Facet States</span></span>  
 [<span data-ttu-id="440f3-112">SQL Server 개체의 정책 기반 관리 패싯 보기</span><span class="sxs-lookup"><span data-stu-id="440f3-112">View the Policy-Based Management Facets on a SQL Server Object</span></span>](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [<span data-ttu-id="440f3-113">XML 파일로 정책 기반 관리 패싯 상태 복사</span><span class="sxs-lookup"><span data-stu-id="440f3-113">Copy a Policy-Based Management Facet State to an XML File</span></span>](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a><span data-ttu-id="440f3-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="440f3-114">See Also</span></span>  
 [<span data-ttu-id="440f3-115">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="440f3-115">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
