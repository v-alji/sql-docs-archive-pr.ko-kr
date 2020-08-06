---
title: 개체 탐색기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.objectexplorer.commandsoptions
- SQL12.SWB.SQLSERVEROBJECTEXPLORER.DHELP
- sql12.swb.objectexplorer.scriptingoptions
- sql12.swb.oe.f1
helpviewer_keywords:
- multi-select [SQL Server Management Studio]
- Registered Servers [SQL Server], Object Explorer
- Query Editor [SQL Server Management Studio], Object Explorer
- connections [SQL Server], SQL Server Management Studio
- servers [SQL Server], Registered Servers
- Object Explorer
- SQL Server Management Studio [SQL Server], connections
- viewing objects
- filtering objects [SQL Server]
- Object Explorer, about Object Explorer
ms.assetid: 469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3acefcd03af1b39d467625800d8837553ff5253b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651437"
---
# <a name="object-explorer"></a><span data-ttu-id="bdde7-102">개체 탐색기</span><span class="sxs-lookup"><span data-stu-id="bdde7-102">Object Explorer</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="bdde7-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]인스턴스의 개체를 관리하는 데 필요한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-103">provides features for managing objects in instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-object-explorer"></a><span data-ttu-id="bdde7-104">개체 탐색기의 이점</span><span class="sxs-lookup"><span data-stu-id="bdde7-104">Benefits of Object Explorer</span></span>  
 <span data-ttu-id="bdde7-105">개체 탐색기는 각 SQL Server 인스턴스에서 개체를 보고 관리하는 계층적 사용자 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-105">Object Explorer provides a hierarchical user interface to view and manage the objects in each instance of SQL Server.</span></span> <span data-ttu-id="bdde7-106">개체 탐색기 정보 창은 인스턴스 개체의 테이블 형식 뷰와 특정 개체를 검색하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-106">The Object Explorer Details pane presents a tabular view of instance objects, and the capability to search for specific objects.</span></span> <span data-ttu-id="bdde7-107">개체 탐색기의 기능은 서버의 유형에 따라 조금씩 다르지만 일반적으로 데이터베이스를 위한 개발 기능과 모든 서버 유형을 위한 관리 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-107">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases, and management features for all server types.</span></span>  
  
## <a name="object-explorer-tasks"></a><span data-ttu-id="bdde7-108">개체 탐색기 태스크</span><span class="sxs-lookup"><span data-stu-id="bdde7-108">Object Explorer Tasks</span></span>  
  
|<span data-ttu-id="bdde7-109">Description</span><span class="sxs-lookup"><span data-stu-id="bdde7-109">Description</span></span>|<span data-ttu-id="bdde7-110">항목</span><span class="sxs-lookup"><span data-stu-id="bdde7-110">Topic</span></span>|  
|-----------------|-----------|  
|<span data-ttu-id="bdde7-111">개체 탐색기를 열고 탐색기의 동작을 정의하는 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-111">Describes how to open the Object Explorer and configure the options that define the behavior of the explorer.</span></span>|[<span data-ttu-id="bdde7-112">개체 탐색기 열기 및 구성</span><span class="sxs-lookup"><span data-stu-id="bdde7-112">Open and Configure Object Explorer</span></span>](open-and-configure-object-explorer.md)|  
|<span data-ttu-id="bdde7-113">개체 탐색기를 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]인스턴스에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-113">Describes how to connect Object Explorer to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|[<span data-ttu-id="bdde7-114">개체 탐색기에서 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="bdde7-114">Connect to an Instance From Object Explorer</span></span>](connect-to-an-instance-from-object-explorer.md)|  
|<span data-ttu-id="bdde7-115">개체 탐색기 계층 구조에서 노드로 표시되는 개체를 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-115">Describes how to manage objects represented as nodes in the Object Explorer hierarchy.</span></span>|[<span data-ttu-id="bdde7-116">개체 탐색기를 사용하여 개체 관리</span><span class="sxs-lookup"><span data-stu-id="bdde7-116">Manage Objects by Using Object Explorer</span></span>](manage-objects-by-using-object-explorer.md)|  
|<span data-ttu-id="bdde7-117">개체 탐색기 정보 창에 대해 설명합니다. 개체 탐색기 정보 창은 서버의 모든 개체를 관리하기 위한 사용자 인터페이스를 제공하는 테이블 형식 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-117">Describes the Object Explorer Details Pane, a tabular view of all of the objects in the server with a user interface to manage them.</span></span>|[<span data-ttu-id="bdde7-118">개체 탐색기 정보 창</span><span class="sxs-lookup"><span data-stu-id="bdde7-118">Object Explorer Details Pane</span></span>](object-explorer-details-pane.md)|  
|<span data-ttu-id="bdde7-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 사용자 지정 보고서를 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bdde7-119">Describes ways to run custom reports in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|[<span data-ttu-id="bdde7-120">Management Studio의 사용자 지정 보고서</span><span class="sxs-lookup"><span data-stu-id="bdde7-120">Custom Reports in Management Studio</span></span>](custom-reports-in-management-studio.md)|  
  
  
