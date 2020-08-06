---
title: Oracle 데이터베이스 속성 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d3cad2735e6cd6095f9730f3b4e7228526451d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649134"
---
# <a name="edit-the-oracle-database-properties"></a><span data-ttu-id="937ca-102">Oracle 데이터베이스 속성 편집</span><span class="sxs-lookup"><span data-stu-id="937ca-102">Edit the Oracle Database Properties</span></span>
  <span data-ttu-id="937ca-103">속성 편집기에서 Oracle 탭을 사용하여 새 인스턴스 마법사의 CDC 데이터베이스 만들기 페이지에 제공한 설명을 변경하고 Oracle 로그 마이닝 데이터베이스 연결 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-103">Use the Oracle tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
 <span data-ttu-id="937ca-104">다음 표에서는 **Oracle** 탭에 표시되는 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-104">The following describes the information in the **Oracle** tab.</span></span>  
  
 <span data-ttu-id="937ca-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="937ca-105">**Name**</span></span>  
 <span data-ttu-id="937ca-106">새 인스턴스 마법사의 CDC 데이터베이스 만들기 페이지에 입력한 CDC 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-106">The name of the CDC Instance that you entered in the Create CDC Database page in the New Instance wizard.</span></span> <span data-ttu-id="937ca-107">이 필드는 읽기 전용이므로 이 정보를 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-107">This field is read only and you cannot edit this information.</span></span>  
  
 <span data-ttu-id="937ca-108">**설명**</span><span class="sxs-lookup"><span data-stu-id="937ca-108">**Description**</span></span>  
 <span data-ttu-id="937ca-109">CDC 인스턴스를 만들 때 새 인스턴스에 대한 설명을 편집하거나 추가하지 않은 경우 설명을 편집하거나 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-109">You can edit the description of the new instance or add one if you did not do so when creating the CDC Instance.</span></span>  
  
 <span data-ttu-id="937ca-110">**Oracle 연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="937ca-110">**Oracle Connect String**</span></span>  
 <span data-ttu-id="937ca-111">사용 중인 Oracle 데이터베이스가 있는 컴퓨터에 대한 Oracle 연결 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-111">The Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="937ca-112">이 필드는 읽기 전용이므로 이 정보를 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-112">This field is read only and you cannot edit this information.</span></span> <span data-ttu-id="937ca-113">연결 문자열을 변경하면 **cdc.xdbcdc_config** 테이블에 저장된 CDC 인스턴스 상태가 손상되어 Oracle CDC 인스턴스가 완전히 다른 Oracle 데이터베이스를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-113">This is because some changes to the connect string may point the Oracle CDC Instance to another Oracle database entirely, corrupting the CDC Instance state as stored in the **cdc.xdbcdc_config** table.</span></span> <span data-ttu-id="937ca-114">약간의 변경이 필요한 경우 SQL Server Management Studio를 사용하여 구성 테이블에서 연결 문자열을 직접 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-114">If minor changes are needed, you can change the connect string directly in the configuration table using SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="937ca-115">**Oracle 로그 마이닝 인증**</span><span class="sxs-lookup"><span data-stu-id="937ca-115">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="937ca-116">로그 마이너를 포함하는 Oracle 데이터베이스에 대한 인증 자격 증명을 입력하려면 **인증**에서 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-116">To enter the authentication credentials for the Oracle database that contains the log miner, select one of the following under **Authentication**:</span></span>  
  
-   <span data-ttu-id="937ca-117">**Windows 인증**: 현재 Windows 도메인 자격 증명을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-117">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="937ca-118">Windows 인증을 사용하도록 Oracle 데이터베이스를 구성한 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-118">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="937ca-119">**Oracle 인증**: 이 옵션을 선택하는 경우 연결 중인 Oracle 데이터베이스의 사용자에 대한 **사용자 이름** 과 **암호** 를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-119">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
 <span data-ttu-id="937ca-120">뷰어에서 Oracle 데이터베이스 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-120">You can view the Oracle database properties in the viewer.</span></span> <span data-ttu-id="937ca-121">뷰어를 사용할 때 정보는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-121">When using the viewer the information is read only.</span></span> <span data-ttu-id="937ca-122">또한 뷰어에는 테이블에서 캡처된 열 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="937ca-122">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="937ca-123">뷰어에 액세스하는 방법은 [How to Manage a CDC Instance](manage-a-cdc-instance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="937ca-123">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937ca-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="937ca-124">See Also</span></span>  
 <span data-ttu-id="937ca-125">[CDC Designer 콘솔에서 CDC Service를 관리하는 방법](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="937ca-125">[How to Manage a CDC Service from the CDC Designer Console](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md) </span></span>  
 <span data-ttu-id="937ca-126">[Oracle 원본 데이터베이스에 연결](connect-to-an-oracle-source-database.md) </span><span class="sxs-lookup"><span data-stu-id="937ca-126">[Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md) </span></span>  
 [<span data-ttu-id="937ca-127">Oracle에 연결</span><span class="sxs-lookup"><span data-stu-id="937ca-127">Connect to Oracle</span></span>](connect-to-oracle.md)  
  
  
