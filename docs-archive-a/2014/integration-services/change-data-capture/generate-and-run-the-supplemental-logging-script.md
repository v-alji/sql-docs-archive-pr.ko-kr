---
title: 보완 로깅 스크립트 생성 및 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728628"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a><span data-ttu-id="c7814-102">보완 로깅 스크립트 생성 및 실행</span><span class="sxs-lookup"><span data-stu-id="c7814-102">Generate and Run the Supplemental Logging Script</span></span>
  <span data-ttu-id="c7814-103">변경 사항을 캡처하기 위한 테이블 선택 페이지를 사용하여 보완 로깅을 설정할 Oracle 원본 데이터베이스에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-103">Use the Set up Tables for Capturing Changes page to run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
 <span data-ttu-id="c7814-104">**보완 로깅 스크립트를 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="c7814-104">**To run the supplemental logging scripts**</span></span>  
  
 <span data-ttu-id="c7814-105">**스크립트 실행** 을 클릭하여 CDC 인스턴스에 대해 정의된 테이블에서 보완 로깅 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-105">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="c7814-106">이 스크립트는 캡처된 테이블에 업데이트 작업을 로깅할 때 트랜잭션 로그에 모든 관련 열을 쓰도록 Oracle 데이터베이스에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-106">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="c7814-107">이 스크립트는 일반적으로 Oracle 시스템 관리자가 검사하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-107">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
 <span data-ttu-id="c7814-108">SQL \* Plus를 사용하여 스크립트를 수동으로 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-108">You can also run the scripts manually using SQL \* Plus.</span></span>  
  
 <span data-ttu-id="c7814-109">**스크립트를 수동으로 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="c7814-109">**To run the scripts manually**</span></span>  
  
 <span data-ttu-id="c7814-110">**복사** 를 클릭하여 스크립트를 클립보드에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-110">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="c7814-111">SQL\* Plus를 열고 Oracle 원본 데이터베이스가 들어 있는 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-111">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="c7814-112">스크립트를 SQL\*Plus에 붙여넣어서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-112">Paste the script into SQL\*Plus to run it.</span></span>  
  
 <span data-ttu-id="c7814-113">보완 로깅 스크립트를 텍스트 파일로 저장하려면 **다른 이름으로 저장** 을 클릭하고 파일을 저장할 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-113">To save the supplemental logging script in a text file, click **Save as** and browse to the location where you want to save the file.</span></span> <span data-ttu-id="c7814-114">파일 이름을 지정하고 **저장** 을 클릭하여 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-114">Give the file a name and click **Save** to save the file.</span></span>  
  
 <span data-ttu-id="c7814-115">**다음** 을 클릭하여 [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7814-115">Click **Next** to [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7814-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7814-116">See Also</span></span>  
 <span data-ttu-id="c7814-117">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="c7814-117">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="c7814-118">보완 로깅 스크립트 검토 및 생성</span><span class="sxs-lookup"><span data-stu-id="c7814-118">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
