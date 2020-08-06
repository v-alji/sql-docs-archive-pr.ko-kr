---
title: SQL Server 이외 구독자 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e36d048b11fcc71b27ab0ab2ee815b0284187c4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651662"
---
# <a name="add-non-sql-server-subscriber"></a><span data-ttu-id="656ab-102">SQL Server 이외 구독자 추가</span><span class="sxs-lookup"><span data-stu-id="656ab-102">Add Non-SQL Server Subscriber</span></span>
  <span data-ttu-id="656ab-103">복제에서는 Oracle 및 IBM DB2 구독자의 스냅샷 및 트랜잭션 게시에 대한 밀어넣기 구독 생성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="656ab-103">Replication supports creating push subscriptions to snapshot and transactional publications for Oracle and IBM DB2 Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="656ab-104">옵션</span><span class="sxs-lookup"><span data-stu-id="656ab-104">Options</span></span>  
 <span data-ttu-id="656ab-105">**추가할 구독자 유형**</span><span class="sxs-lookup"><span data-stu-id="656ab-105">**Type of Subscriber to add**</span></span>  
 <span data-ttu-id="656ab-106">Oracle 구독자 또는 IBM DB2 구독자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="656ab-106">Select an Oracle Subscriber or IBM DB2 Subscriber.</span></span> <span data-ttu-id="656ab-107">이러한 구독자 지원에 대한 자세한 내용은 [SQL Server 이외 구독자](non-sql/non-sql-server-subscribers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="656ab-107">For more information about support for these Subscribers, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
 <span data-ttu-id="656ab-108">**데이터 원본 이름**</span><span class="sxs-lookup"><span data-stu-id="656ab-108">**Data source name**</span></span>  
 <span data-ttu-id="656ab-109">네트워크에서 데이터베이스를 찾는 데 사용되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="656ab-109">The name used to locate the database on a network.</span></span> <span data-ttu-id="656ab-110">복제에서는 로그인, 암호 및 이 마법사의 **배포 에이전트 보안** 페이지에서 지정한 연결 옵션과 결합된 데이터 원본 이름을 사용하여 데이터베이스에 대한 연결 문자열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="656ab-110">Replication produces a connection string for the database using the data source name, combined with the login, password, and any connection options you specify in the **Distribution Agent Security** page in this wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="656ab-111">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 배포 에이전트가 구독을 초기화할 때까지 데이터 원본 이름과 연결 문자열의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="656ab-111">The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656ab-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="656ab-112">See Also</span></span>  
 <span data-ttu-id="656ab-113">[SQL Server 이외 구독자에 대한 구독 만들기](create-a-subscription-for-a-non-sql-server-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="656ab-113">[Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md) </span></span>  
 <span data-ttu-id="656ab-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span><span class="sxs-lookup"><span data-stu-id="656ab-114">[Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md) </span></span>  
 [<span data-ttu-id="656ab-115">게시 구독</span><span class="sxs-lookup"><span data-stu-id="656ab-115">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
