---
title: Oracle에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6546e3bbde666107ed7757c41d98d5b7b598924
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738638"
---
# <a name="connect-to-oracle"></a><span data-ttu-id="7fe66-102">Oracle에 연결</span><span class="sxs-lookup"><span data-stu-id="7fe66-102">Connect to Oracle</span></span>
  <span data-ttu-id="7fe66-103">CDC 인스턴스에 사용되는 테이블을 처음으로 추가하거나 편집하는 경우 Oracle 데이터베이스에 연결하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-103">When you add or edit the tables used in the CDC instance for the first time, you may be asked to connect to the Oracle database.</span></span> <span data-ttu-id="7fe66-104">캡처할 테이블의 스키마에 액세스할 수 있는 Oracle 사용자의 자격 증명을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-104">You should enter the credentials of an Oracle user who can access the schema of the tables to be captured.</span></span> <span data-ttu-id="7fe66-105">이 대화 상자에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-105">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="7fe66-106">**인증**</span><span class="sxs-lookup"><span data-stu-id="7fe66-106">**Authentication**</span></span>  
  
 <span data-ttu-id="7fe66-107">다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-107">Select one of the following:</span></span>  
  
-   <span data-ttu-id="7fe66-108">**Windows 인증**: 현재 Windows 도메인 자격 증명을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-108">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="7fe66-109">Windows 인증을 사용하도록 Oracle 데이터베이스를 구성한 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-109">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="7fe66-110">**Oracle 인증**: 이 옵션을 선택하는 경우 연결 중인 Oracle 데이터베이스의 사용자에 대한 **사용자 이름** 과 **암호** 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe66-110">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe66-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fe66-111">See Also</span></span>  
 [<span data-ttu-id="7fe66-112">CDC 인스턴스에 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="7fe66-112">Add Tables to a CDC Instance</span></span>](add-tables-to-a-cdc-instance.md)  
  
  
