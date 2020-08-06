---
title: INFORMATION_SCHEMA. SCHEMATA는 인스턴스의 데이터베이스가 아니라 데이터베이스의 스키마 이름을 반환 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cb2a34a59bf6257c188210fc7bf2aeacb70f6b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660295"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a><span data-ttu-id="c5697-102">INFORMATION_SCHEMA.SCHEMATA는 인스턴스의 데이터베이스가 아니라 데이터베이스의 스키마 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-102">INFORMATION_SCHEMA.SCHEMATA returns schema names in a database, not databases in an instance</span></span>
  <span data-ttu-id="c5697-103">업그레이드 관리자가 INFORMATION_SCHEMA.SCHEMATA 뷰를 참조하는 문을 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-103">Upgrade Advisor detected statements that reference the INFORMATION_SCHEMA.SCHEMATA view.</span></span> <span data-ttu-id="c5697-104">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 뷰가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 데이터베이스를 반환했지만</span><span class="sxs-lookup"><span data-stu-id="c5697-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5697-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 데이터베이스의 모든 스키마를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, the view returns all schemas in a database.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c5697-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="c5697-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c5697-107">Description</span><span class="sxs-lookup"><span data-stu-id="c5697-107">Description</span></span>  
 <span data-ttu-id="c5697-108">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 INFORMATION_SCHEMA.SCHEMATA 뷰가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 데이터베이스를 반환했지만</span><span class="sxs-lookup"><span data-stu-id="c5697-108">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the INFORMATION_SCHEMA.SCHEMATA view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5697-109">이제 뷰에서 SQL 표준을 준수하는 데이터베이스의 모든 스키마가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-109">Now, the view returns all schemas in a database, which complies with the SQL Standard.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c5697-110">수정 동작</span><span class="sxs-lookup"><span data-stu-id="c5697-110">Corrective Action</span></span>  
 <span data-ttu-id="c5697-111">인스턴스의 모든 데이터베이스를 반환 하도록 응용 프로그램을 수정 하 여 **sys.debug** 카탈로그 뷰를 참조 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c5697-111">Modify your application to reference the **sys.databases** catalog view to return all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5697-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5697-112">See Also</span></span>  
 <span data-ttu-id="c5697-113">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c5697-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c5697-114">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="c5697-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
