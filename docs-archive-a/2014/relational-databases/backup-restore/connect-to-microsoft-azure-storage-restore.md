---
title: Azure Storage에 연결 (복원) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dff9730d6592381b1c8e8a1cf7ee45ad7532a440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661180"
---
# <a name="connect-to-azure-storage-restore"></a><span data-ttu-id="9ab63-102">Azure Storage에 연결(복원)</span><span class="sxs-lookup"><span data-stu-id="9ab63-102">Connect to Azure Storage (Restore)</span></span>
  <span data-ttu-id="9ab63-103">대화 상자를 사용하면 Azure Storage 계정에서 파일 스토리지를 검색하기 위해 Azure Storage 계정 정보에 대한 연결을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-103">The dialog box allows you to specify the connection to Azure storage account information in order to retrieve the files storage in the Azure storage account.</span></span> <span data-ttu-id="9ab63-104">필요한 정보를 지정한 후 **연결**을 클릭하여 Azure Storage에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-104">After specifying the required information, click **Connect** to establish the connection to Azure storage.</span></span>  
  
## <a name="azure-storage-account"></a><span data-ttu-id="9ab63-105">Azure Storage 계정</span><span class="sxs-lookup"><span data-stu-id="9ab63-105">Azure Storage Account</span></span>  
 <span data-ttu-id="9ab63-106">**스토리지 계정**</span><span class="sxs-lookup"><span data-stu-id="9ab63-106">**Storage account**</span></span>  
 <span data-ttu-id="9ab63-107">사용할 Azure Storage 계정 이름을 선택, 입력 또는 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-107">Select, type or paste the name of the Azure storage account you want to use.</span></span> <span data-ttu-id="9ab63-108">드롭다운 상자에 이전에 사용한 계정이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-108">The drop down box lists the accounts previously used.</span></span>  
  
 <span data-ttu-id="9ab63-109">**계정 키**</span><span class="sxs-lookup"><span data-stu-id="9ab63-109">**Account key**</span></span>  
 <span data-ttu-id="9ab63-110">Azure Storage 계정 액세스 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-110">Specify the Azure storage account access key.</span></span>  
  
 <span data-ttu-id="9ab63-111">**보안 엔드포인트 사용(HTTPS)** 확인란</span><span class="sxs-lookup"><span data-stu-id="9ab63-111">**Use secure endpoints (HTTPS)** check box</span></span>  
 <span data-ttu-id="9ab63-112">Azure Storage에 대한 보안 연결을 설정하려면 이 옵션을 선택합니다(권장 사항).</span><span class="sxs-lookup"><span data-stu-id="9ab63-112">Select this option to make a secure connection to Azure storage - recommended.</span></span>  
  
 <span data-ttu-id="9ab63-113">**계정 키 저장** 확인란</span><span class="sxs-lookup"><span data-stu-id="9ab63-113">**Save account key** check box</span></span>  
 <span data-ttu-id="9ab63-114">SQL Server에서 이 스토리지 계정에 대한 액세스 키를 기억하도록 설정하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-114">Select this check box if you want SQL Server to remember the access key for this storage account.</span></span>  
  
### <a name="sql-credential"></a><span data-ttu-id="9ab63-115">SQL 자격 증명</span><span class="sxs-lookup"><span data-stu-id="9ab63-115">SQL Credential</span></span>  
 <span data-ttu-id="9ab63-116">**기존 자격 증명 선택**</span><span class="sxs-lookup"><span data-stu-id="9ab63-116">**Select an existing credential**</span></span>  
 <span data-ttu-id="9ab63-117">스토리지 계정 및 계정 키 정보와 일치하는 기존 SQL 자격 증명을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-117">Select an existing SQL Credential that matches the storage account and account key information.</span></span>  
  
 <span data-ttu-id="9ab63-118">**새 자격 증명 만들기**</span><span class="sxs-lookup"><span data-stu-id="9ab63-118">**Create a new Credential**</span></span>  
 <span data-ttu-id="9ab63-119">스토리지 계정 및 계정 키 정보를 사용하여 새 자격 증명을 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-119">Select this option to create a new credential using the storage account and account key information.</span></span> <span data-ttu-id="9ab63-120">**자격 증명 이름** 필드에서 새 자격 증명 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ab63-120">Specify the name of the new credential in the **Credential Name** field.</span></span>  
  
  
