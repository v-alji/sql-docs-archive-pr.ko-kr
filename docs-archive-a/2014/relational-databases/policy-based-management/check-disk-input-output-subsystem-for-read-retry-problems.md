---
title: 읽기 다시 시도 문제에 대 한 디스크 입력 출력 하위 시스템 확인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19809b1554e435600eb4eeae424bed17dc27bdbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728227"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a><span data-ttu-id="b7ab7-102">읽기 다시 시도 문제에 대한 디스크 입력-출력 하위 시스템 검사</span><span class="sxs-lookup"><span data-stu-id="b7ab7-102">Check Disk Input Output Subsystem for Read Retry Problems</span></span>
  <span data-ttu-id="b7ab7-103">이 규칙은 이벤트 로그에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 메시지 825를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-103">This rule checks the event log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message 825.</span></span> <span data-ttu-id="b7ab7-104">이 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 디스크에서 데이터를 읽으려는 첫 번째 시도가 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was unable to read data from the disk on the first try.</span></span> <span data-ttu-id="b7ab7-105">이 메시지는 디스크 I/O 하위 시스템에 중요한 문제가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-105">This message indicates a major problem with the disk I/O subsystem.</span></span> <span data-ttu-id="b7ab7-106">이 메시지는 현재까지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문제를 나타내는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-106">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem.</span></span> <span data-ttu-id="b7ab7-107">하지만 문제가 해결되지 않을 경우 디스크 문제로 인해 데이터 손실 또는 데이터베이스 손상이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-107">However, the disk problem could cause data loss or database corruption if it is not resolved.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b7ab7-108">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="b7ab7-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="b7ab7-109">다음은 기본 하드웨어 문제를 확인하고 해결하는 데 도움이 되는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-109">The following actions might help you discover and resolve the underlying hardware problem:</span></span>  
  
-   <span data-ttu-id="b7ab7-110">이 메시지의 오류 로그 및 변수 텍스트를 검토하여 문제를 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-110">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="b7ab7-111">디스크 시스템을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-111">Check the disk system.</span></span> <span data-ttu-id="b7ab7-112">디스크, 디스크 컨트롤러, 배열 카드 또는 디스크 드라이버에 관련된 문제일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-112">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="b7ab7-113">최신 유틸리티의 디스크 제조업체에 문의하여 디스크 시스템 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-113">Contact the disk manufacturer for the latest utilities for checking the status of the disk system.</span></span>  
  
-   <span data-ttu-id="b7ab7-114">최신 드라이버 업데이트에 대해 디스크 제조업체에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="b7ab7-114">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b7ab7-115">참조 항목</span><span class="sxs-lookup"><span data-stu-id="b7ab7-115">For More Information</span></span>  
 [<span data-ttu-id="b7ab7-116">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="b7ab7-116">MSSQLSERVER_825</span></span>](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 <span data-ttu-id="b7ab7-117">[SQL Server I/O 기본 사항, 2장(SQL Server I/O Basics, Chapter 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="b7ab7-117">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
