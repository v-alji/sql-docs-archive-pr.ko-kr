---
title: SQL Server 유틸리티에 연결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647683"
---
# <a name="connect-to-a-sql-server-utility"></a><span data-ttu-id="727b5-102">SQL Server 유틸리티에 연결</span><span class="sxs-lookup"><span data-stu-id="727b5-102">Connect to a SQL Server Utility</span></span>
  <span data-ttu-id="727b5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 연결하려면 먼저 UCP(유틸리티 제어 지점)를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-103">Before you can connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="727b5-104">자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="727b5-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>

 <span data-ttu-id="727b5-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스 상태를 보고 관리하려면 SSMS( [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] )를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-105">To view and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource health, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>

 <span data-ttu-id="727b5-106">SSMS를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="727b5-106">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility through SSMS:</span></span>

1.  <span data-ttu-id="727b5-107">SSMS를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-107">Launch SSMS.</span></span>

2.  <span data-ttu-id="727b5-108">SSMS에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-108">In SSMS, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

3.  <span data-ttu-id="727b5-109">**보기** 를 클릭한 다음 **유틸리티 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-109">Click **View** and then **Utility Explorer**.</span></span>

4.  <span data-ttu-id="727b5-110">유틸리티 탐색기 탐색 창에서 ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**유틸리티에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-110">In the Utility Explorer navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span>

5.  <span data-ttu-id="727b5-111">**서버에 연결** 대화 상자에서 UCP 인스턴스 이름을 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-111">In the **Connect to Server** dialog box, specify the UCP instance name, then click **Connect**.</span></span>

6.  <span data-ttu-id="727b5-112">UCP의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에 대한 트리 뷰를 보려면 유틸리티 탐색기 탐색 창을 보면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-112">View the Utility Explorer Navigation Pane to see a tree view of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources in the UCP.</span></span>

 <span data-ttu-id="727b5-113">새 UCP를 만들어도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="727b5-113">Creating a new UCP also connects you to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="727b5-114">자세한 내용은 [SQL Server 유틸리티 제어 지점 만들기&#40;SQL Server 유틸리티&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="727b5-114">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="727b5-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="727b5-115">See Also</span></span>
 <span data-ttu-id="727b5-116">[SQL Server 유틸리티 기능 및 작업](sql-server-utility-features-and-tasks.md) [Resource Health 정책 결과 &#40;SQL Server 유틸리티&#41;](view-resource-health-policy-results-sql-server-utility.md)</span><span class="sxs-lookup"><span data-stu-id="727b5-116">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md)</span></span>


