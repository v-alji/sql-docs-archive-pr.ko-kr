---
title: 보완 로깅 스크립트 검토 및 생성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- scripts
ms.assetid: 5c858ae2-37d6-42e8-a252-7f6ed4e628a7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb735c0ee318ac68d48c71c09fc76ec305eb2552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649133"
---
# <a name="review-and-generate-supplemental-logging-scripts"></a><span data-ttu-id="ca0d0-102">보완 로깅 스크립트 검토 및 생성</span><span class="sxs-lookup"><span data-stu-id="ca0d0-102">Review and Generate Supplemental Logging Scripts</span></span>
  <span data-ttu-id="ca0d0-103">**스크립트** 탭을 사용하여 보완 로깅을 설정하는 Oracle 원본 데이터베이스에서 스크립트를 실행하거나 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-103">Use the **Scripts** tab to run or re-run a script on the Oracle source database that sets up supplemental logging.</span></span>  
  
 <span data-ttu-id="ca0d0-104">스크립트를 실행하기 전에 다음 중 하나를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-104">Before you run the scripts select one of the following:</span></span>  
  
 <span data-ttu-id="ca0d0-105">**이 세션에 변경 내용 포함**</span><span class="sxs-lookup"><span data-stu-id="ca0d0-105">**Include changes in this session**</span></span>  
 <span data-ttu-id="ca0d0-106">CDC 인스턴스에 추가된 새 테이블 또는 속성 편집기를 사용하여 변경한 테이블에서 스크립트를 실행하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-106">Select this to run the script on any new table that was added to the CDC instance or on tables that were changed in any way using the Properties editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca0d0-107">CDC 인스턴스에서 테이블이 변경되지 않은 경우 Oracle 보완 로깅 스크립트 영역이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-107">If no changes were made to the tables in the CDC instance, the Oracle supplemental logging script area will be empty.</span></span>  
  
 <span data-ttu-id="ca0d0-108">**모든 테이블/캡처 인스턴스 포함**</span><span class="sxs-lookup"><span data-stu-id="ca0d0-108">**Include all tables/capture instances**</span></span>  
 <span data-ttu-id="ca0d0-109">CDC 인스턴스의 모든 테이블 및 캡처 인스턴스에 대해 스크립트를 실행하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-109">Select this to run the script on all of the tables and capture instances in the CDC instance.</span></span>  
  
 <span data-ttu-id="ca0d0-110">이러한 옵션 중 하나를 선택 후 보완 로깅 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-110">After you select one of these options, run the supplemental logging script.</span></span>  
  
### <a name="to-run-the-supplemental-logging-scripts"></a><span data-ttu-id="ca0d0-111">보완 로깅 스크립트를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="ca0d0-111">To run the supplemental logging scripts</span></span>  
  
1.  <span data-ttu-id="ca0d0-112">**스크립트 실행** 을 클릭하여 CDC 인스턴스에 대해 정의된 테이블에서 보완 로깅 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-112">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="ca0d0-113">이 스크립트는 캡처된 테이블에 업데이트 작업을 로깅할 때 트랜잭션 로그에 모든 관련 열을 쓰도록 Oracle 데이터베이스에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-113">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="ca0d0-114">이 스크립트는 일반적으로 Oracle 시스템 관리자가 검사하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-114">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
2.  <span data-ttu-id="ca0d0-115">보완 로깅 스크립트를 실행하면 유효한 Oracle 사용자 이름과 암호를 입력할 수 있는 스크립트 실행을 위한 Oracle 자격 증명 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-115">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="ca0d0-116">적절한 Oracle 자격 증명을 제공하는 방법은 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-116">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="ca0d0-117">필요한 경우 SQL \* Plus를 사용하여 스크립트를 수동으로 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-117">You can also run the scripts manually using SQL \* Plus, if necessary.</span></span>  
  
### <a name="to-run-the-scripts-manually"></a><span data-ttu-id="ca0d0-118">스크립트를 수동으로 실행하려면</span><span class="sxs-lookup"><span data-stu-id="ca0d0-118">To run the scripts manually</span></span>  
  
1.  <span data-ttu-id="ca0d0-119">**복사** 를 클릭하여 스크립트를 클립보드에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-119">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="ca0d0-120">SQL\* Plus를 열고 Oracle 원본 데이터베이스가 들어 있는 디렉터리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-120">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="ca0d0-121">스크립트를 SQL\*Plus에 붙여넣어서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-121">Paste the script into SQL\*Plus to run it.</span></span>  
  
### <a name="to-save-the-supplemental-logging-script-in-a-text-file"></a><span data-ttu-id="ca0d0-122">텍스트 파일에 보완 로깅 스크립트를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="ca0d0-122">To save the supplemental logging script in a text file</span></span>  
  
1.  <span data-ttu-id="ca0d0-123">**다른 이름으로 저장** 을 클릭하고 파일을 저장할 위치로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-123">Click **Save as** and browse to the location where you want to save the file.</span></span>  
  
2.  <span data-ttu-id="ca0d0-124">파일 이름을 지정하고 **저장** 을 클릭하여 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ca0d0-124">Give the file a name and click **Save** to save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0d0-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca0d0-125">See Also</span></span>  
 <span data-ttu-id="ca0d0-126">[CDC 인스턴스 속성을 편집하는 방법](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ca0d0-126">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="ca0d0-127">스크립트 실행을 위한 Oracle 자격 증명</span><span class="sxs-lookup"><span data-stu-id="ca0d0-127">Oracle Credentials for Running Script</span></span>](oracle-credentials-for-running-script.md)  
  
  
