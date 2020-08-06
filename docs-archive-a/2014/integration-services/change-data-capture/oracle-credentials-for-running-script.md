---
title: 스크립트 실행을 위한 Oracle 자격 증명 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 683b313e5b1065c3709c4637ddf968641612cc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728583"
---
# <a name="oracle-credentials-for-running-script"></a><span data-ttu-id="33cb8-102">스크립트 실행을 위한 Oracle 자격 증명</span><span class="sxs-lookup"><span data-stu-id="33cb8-102">Oracle Credentials for Running Script</span></span>
  <span data-ttu-id="33cb8-103">Oracle CDC Designer 콘솔에서 Oracle 보완 로깅 스크립트를 실행하면 스크립트를 실행 중인 Oracle 사용자의 자격 증명을 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-103">To run the Oracle supplemental logging script from the Oracle CDC Designer console, the program prompts you for the credentials of the Oracle user who is running the script.</span></span> <span data-ttu-id="33cb8-104">이 스크립트를 실행하려면 캡처할 모든 테이블에 대한 ALTER TABLE 권한과 DBA_LOG_GROUPS 뷰에 대한 SELECT 권한이 Oracle 사용자에게 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-104">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="33cb8-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="33cb8-105">Task List</span></span>  
 <span data-ttu-id="33cb8-106">이 대화 상자에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-106">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="33cb8-107">**인증**</span><span class="sxs-lookup"><span data-stu-id="33cb8-107">**Authentication**</span></span>  
  
 <span data-ttu-id="33cb8-108">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-108">Select one of the following:</span></span>  
  
-   <span data-ttu-id="33cb8-109">**Windows 인증**: 현재 Windows 도메인 자격 증명을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-109">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="33cb8-110">Windows 인증을 사용하도록 Oracle 데이터베이스를 구성한 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-110">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="33cb8-111">**Oracle 인증**: 이 옵션을 선택하는 경우 연결 중인 원본 Oracle 데이터베이스에 사용자의 **사용자 이름** 과 **암호** 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33cb8-111">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Source Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cb8-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33cb8-112">See Also</span></span>  
 <span data-ttu-id="33cb8-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="33cb8-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="33cb8-114">보완 로깅 스크립트 검토 및 생성</span><span class="sxs-lookup"><span data-stu-id="33cb8-114">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
