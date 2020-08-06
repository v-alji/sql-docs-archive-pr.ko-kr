---
title: Oracle 보완 로깅 스크립트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0aa55e71c17574eba9e25e098a3881b0eb4c9e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728580"
---
# <a name="oracle-supplemental-logging-script"></a><span data-ttu-id="e40be-102">Oracle 보완 로깅 스크립트</span><span class="sxs-lookup"><span data-stu-id="e40be-102">Oracle Supplemental Logging Script</span></span>
  <span data-ttu-id="e40be-103">이 대화 상자에는 Oracle 보완 로깅 스크립트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-103">This dialog box shows the script the Oracle supplemental logging script.</span></span>  
  
 <span data-ttu-id="e40be-104">사용할 CDC 인스턴스를 준비할 때 CDC Designer는 캡처할 테이블에 대한 보완 로깅을 설정하는 Oracle SQL 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-104">When you prepare a CDC Instance for use, the CDC Designer creates an Oracle SQL script that sets up supplemental logging for the tables to be captured.</span></span> <span data-ttu-id="e40be-105">보완 로깅 스크립트는 특정 테이블이 업데이트될 경우 트랜잭션 로그에 기록되는 변경 레코드에 변경된 열뿐만 아니라 관련 열의 데이터도 모두 포함되도록 Oracle에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-105">The supplemental logging script tells Oracle that when a specific table is updated, the change records it writes to the transaction log should contain the data of all columns of interest, not just the columns that changed.</span></span>  
  
 <span data-ttu-id="e40be-106">조직의 Oracle DBA 정책에 따라 보완 로깅 스크립트를 실행하려면 Oracle DBA의 검토와 승인이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-106">Depending on the Oracle DBA policies in your organization, running the supplemental logging script may require a review and approval by an Oracle DBA.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e40be-107">옵션</span><span class="sxs-lookup"><span data-stu-id="e40be-107">Options</span></span>  
 <span data-ttu-id="e40be-108">다음은 스크립트를 실행하는 방법을 지정하는 데 사용할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-108">The following are the available options for how to execute the script.</span></span>  
  
 <span data-ttu-id="e40be-109">**스크립트 실행**</span><span class="sxs-lookup"><span data-stu-id="e40be-109">**Run Script**</span></span>  
 <span data-ttu-id="e40be-110">CDC 인스턴스에 대해 정의된 테이블에서 보완 로깅 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-110">Runs the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="e40be-111">이 스크립트를 실행하려면 캡처할 모든 테이블에 대한 ALTER TABLE 권한과 DBA_LOG_GROUPS 뷰에 대한 SELECT 권한이 Oracle 사용자에게 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-111">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span> <span data-ttu-id="e40be-112">또한 Oracle 사용자에게 필요한 사용 권한과 함께 Oracle 데이터베이스 사용을 위한 자격 증명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-112">In addition, the Oracle user must have the credentials for an Oracle database use with the required permissions.</span></span> <span data-ttu-id="e40be-113">프로그램에서 Oracle 자격 증명을 묻는 메시지를 표시한 다음 스크립트를 실행하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-113">You can let the program prompt you for the Oracle credentials and then have it run the script.</span></span>  
  
 <span data-ttu-id="e40be-114">**다른 이름으로 저장**</span><span class="sxs-lookup"><span data-stu-id="e40be-114">**Save As**</span></span>  
 <span data-ttu-id="e40be-115">스크립트를 텍스트 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-115">Saves the script to a text file.</span></span> <span data-ttu-id="e40be-116">Oracle 데이터베이스 관리자(DBA)가 보완 로깅 스크립트를 검사하고 실행해야 하는 경우에 사용되며, 스크립트를 텍스트 파일로 저장하여 나중에 전자 메일 또는 다른 방법으로 Oracle DBA에게 보낸 다음 Oracle 데이터베이스에서 스크립트를 실행하는 데 사용되는 SQL\*Plus Oracle 유틸리티 또는 기타 도구를 사용하여 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-116">This is used if an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script, the program lets you save the script to a text file that you can later send to the Oracle DBA by email or by other means to be execute later (by using the SQL\*Plus Oracle utility or other tool for running scripts on an Oracle database).</span></span>  
  
 <span data-ttu-id="e40be-117">**Copy**</span><span class="sxs-lookup"><span data-stu-id="e40be-117">**Copy**</span></span>  
 <span data-ttu-id="e40be-118">스크립트를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-118">Copies the script to the clipboard.</span></span> <span data-ttu-id="e40be-119">Oracle 데이터베이스 관리자가 보완 로깅 스크립트를 검사하고 실행해야 하는 경우에 필요한 위치에 스크립트를 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e40be-119">When ready you can paste the script in any location you need in case an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40be-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e40be-120">See Also</span></span>  
 <span data-ttu-id="e40be-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e40be-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="e40be-122">CDC 인스턴스 관리</span><span class="sxs-lookup"><span data-stu-id="e40be-122">Manage a CDC Instance</span></span>](manage-a-cdc-instance.md)  
  
  
